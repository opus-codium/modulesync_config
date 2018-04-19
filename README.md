# Opus-Codium ModuleSync Configuration

This repository contains the configuration of
[modulesync](http://github.com/puppetlabs/modulesync) for the Opus-Codium
puppet modules.

A full description of ModuleSync can be found in [ModuleSync's
README](https://github.com/puppetlabs/modulesync).

## How to use this repository?

Clone this repository, hack whatever you want to change, and see what would
happen with:

```
bundle exec msync update --noop
```

When you are happy with your changes, commit them into *this* repository, tag a
new version and publish it.

```
git add .
git commit -m 'Add this awesome feature :heart:'
git push
git tag -s '0.0.0'
git push --tags
```

You are now ready to push your changes to all modules repositories:

```
bundle exec msync update
```

This should trigger a bunch of Travis-CI builds.  While waiting for completion
and problems to fix, you can open pull-requests:

```
./bin/create-pull-requests
```

## How to add a module?

Add the module to the `managed_modules.yml` file.  Keep this file sorted
alphabetically.
