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

When you are happy with your changes, commit them into *this* repository.

You are now ready to push your changes to all modules repositories:

```
bundle exec msync update --pr --pr-title 'Add this awesome feature :heart:'
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
