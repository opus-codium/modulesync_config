# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/)
and this project adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

## [1.2.0] - 2020-01-22
### Added
- Add `bin/rebase-on-master` script;
- Add `bin/squash-all-commits` script.

### Changed
- Check that module parameters have a type;
- Check that module parameters are documented;
- Check the metadata.json file;
- Update the list of modules we manage.

## [1.1.1] - 2019-11-27
### Added
- Add `puppet-tls_checker` to the list of modules.

### Changed
- Rename the Layout/AlignHash cop to Layout/HashAlignment.

## [1.1.0] - 2019-05-19
### Added
- Add `puppet-certificate_checker` to the list of modules.

### Changed
- Disable the Style/FrozenStringLiteralComment cop,
- Align versions of Ruby used for CI with those packaged in puppet-agent.

## [1.0.0] - 2018-12-03
### Initial release

[Unreleased]: https://github.com/opus-codium/modulesync_config/compare/1.2.1...master
[1.2.0]: https://github.com/opus-codium/modulesync_config/compare/1.1.1...1.2.0
[1.1.1]: https://github.com/opus-codium/modulesync_config/compare/1.1.0...1.1.1
[1.1.0]: https://github.com/opus-codium/modulesync_config/compare/1.0.0...1.1.0
