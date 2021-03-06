---
description: A commonly-used macOS package manager
---
# Homebrew


## Resources

- [Homebrew Cheatsheet](https://devhints.io/homebrew) on _DevHints_.
- [Homebrew docs](https://docs.brew.sh/) homepage
- [Homebrew Tips N' Tricks](https://docs.brew.sh/Tips-N%27-Tricks) in the docs


## Install brew

See the [brew.sh](https://brew.sh) homepage.


## Update list

Update Homebrew's package list - this does _not_ actually update packages. Note you probably don't need to use this since an update is done before commands like install.

```sh
$ brew update
```


## Manage packages

### Install package

Install a specific package by its formula.

_Note: Unlike `apt`, the `update` command is done internally to get the latest remote info - [#1670](https://github.com/Homebrew/brew/issues/1670)._

```sh
$ brew install PACKAGE
$ brew install PACKAGE@VERSION  # e.g. gcc@7 python@3.9
```

_Warning: The install command will also upgrade all installed packages._

Install without auto-upgrade - from [article](https://computingforgeeks.com/prevent-homebrew-auto-update-on-macos/).

```sh
$ HOMEBREW_NO_AUTO_UPDATE=1 brew install PACKAGE
```

Set in `.bashrc` or `.zshrc`.

```sh
$ export HOMEBREW_NO_AUTO_UPDATE=1
```

### Install cask

See also [Homebrew casks](https://formulae.brew.sh/cask/).

```sh
$ brew cask install CASK_NAME
```

## Upgrade


### Upgrade one package

```sh
$ brew upgrade PACKAGE
```

## Upgrade all packages

Update outdated packages. WARNING Use this with caution - it can break Python virtual environments for example.

```sh
$ brew upgrade --dry-run

$ brew upgrade
```


Here is a shortcut I found - from [article](https://medium.com/@kkostov/how-to-install-node-and-npm-on-macos-using-homebrew-708e2c3877bd ).

```sh
alias brewery='brew update && brew upgrade && brew cleanup'
```

### Help

```sh
$ brew upgrade --help
```
```
Upgrade outdated, unpinned formulae using the same options they were originally
installed with, plus any appended brew formula options. If formula are
specified, upgrade only the given formula kegs (unless they are pinned; see
pin, unpin).

Unless HOMEBREW_NO_INSTALL_CLEANUP is set, brew cleanup will then be run for
the upgraded formulae or, every 30 days, for all formulae.
```


## Taps

```sh
$ brew tap <TAP_NAME>/taps
$ brew install <TAP_NAME>
```

e.g.

```sh
$ brew tap isacikgoz/taps
$ brew install gitbatch
```
