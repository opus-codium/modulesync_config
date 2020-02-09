# frozen_string_literal: true

require 'erb'
require 'open3'
require 'rubocop/rake_task'
require 'yaml'

RuboCop::RakeTask.new

desc 'Check syntax of various files'
task default: %i[erb rubocop yml]

task :erb do
  puts '===> Checking ERB files syntax…'
  (Dir['**/.*.erb', '**/*.erb']).each do |file|
    puts "---> #{file}"
    erb = File.read(file)
    code = ERB.new(erb, nil, '-').src
    Open3.popen2e('ruby -c') do |stdin, stdout_and_stderr, wait_thr|
      stdin.puts(code)
      stdin.close

      exit_status = wait_thr.value
      abort(stdout_and_stderr.read) unless exit_status.success?

      stdout_and_stderr.close
    end
  end
end

task :yml do
  puts '===> Checking YAML files syntax…'
  (Dir['**/.*.yml', '**/*.yml']).each do |file|
    puts "---> #{file}"

    begin
      YAML.load_file(file)
    rescue Psych::SyntaxError => e
      abort(e.message)
    end
  end
end

require 'github_changelog_generator/task'

GitHubChangelogGenerator::RakeTask.new :changelog do |config|
  config.user = 'opus-codium'
  config.project = 'modulesync_config'
end
