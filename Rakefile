# frozen_string_literal: true

require 'erb'
require 'find'
require 'open3'
require 'rubocop/rake_task'
require 'yaml'

def project_files(*suffixes, &block)
  Find.find(*Dir['*']) do |path|
    if FileTest.directory?(path)
      Find.prune if %w[modules vendor].include?(path)
    elsif suffixes.map { |x| path.end_with?(x) }.any?
      block.call(path)
    end
  end
end

RuboCop::RakeTask.new

desc 'Check syntax of various files'
task default: %i[erb rubocop yml]

task :erb do
  puts '===> Checking ERB files syntax…'
  project_files('.erb') do |file|
    puts file
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
  project_files('.yml', '.yaml') do |file|
    puts file

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
  config.future_release = '2.1.0'
  config.unreleased = true
  config.exclude_labels = %w[duplicate question invalid wontfix wont-fix modulesync skip-changelog ignore]
end
