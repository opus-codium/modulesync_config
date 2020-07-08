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
new version, ensure the changes are documented, and publish the update:

```
git add .
git commit -m 'Add this awesome feature :heart:'
vim Rakefile # Update future_release of the changelog task
bundle exec rake changelog
git add Rakefile CHANGELOG.md
git commit -m 'Prepare for 0.0.0'
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

If a remote branch `modulesync` existed in a repo, commits will be added on top
of it, and the branch will not include recent work on master.  To rebase all
branches on top of master use:

```
./bin/rebase-on-master
```

Feel free to manually add commits in the `modulesync` branch until the CI is
happy with your changes.  When you are ready, merge your Pull Request, and
remove the `modulesync` branch.

## How to add a module?

Add the module to the `managed_modules.yml` file.  Keep this file sorted
alphabetically.
