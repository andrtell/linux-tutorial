[Back to top](README.md)

# APT Tutorial
Ubuntu (Debian) package manager tutorial and cheat-sheet

```
man apt
```
Most of what follows is a summary (or copy) of the various man pages for the `apt` package system.

## User CLI

The `apt` command is designed as an end-user tool. 

All features of `apt` are available in tools like `apt-get` and `apt-cache` (offers more control).

### System
These commands work on the system as a whole.
```
apt update
```
Download package information from all configured sources.
```
apt list --installed
```
List installed packages.
```
apt list --upgradable
```
List packages that can be upgraded.
```
apt upgrade
```
Install available upgrades of all packages installed.
```
apt full-upgrade
```
Install upgrades and also remove installed packages if needed to upgrade system.
```
apt autoremove
```
Remove packages that are no longer needed.


### Sources
To install a package from a source that is maintained by a third-party, your first need to add that source.
```
man add-apt-repository
```
Sources can be added or removed by using the `add-apt-repository` command.
```
add-apt-repository -P neovim-ppa/stable
```
Add a new PPA source.
```
apt update
apt install neovim
```
Do not forget to run `apt update` after adding a source.
```
add-apt-repository -P -r neovim-ppa/stable
```
Remove a PPA source.

```
add-apt-repository -L | less
```
List APT sources.
```
ls /etc/apt/sources.list.d/*
```
See `man sources.list` for working with sources as files.

### Packages

```
apt search --names-only `^neovim$`

neovim/noble,now 0.9.5-6ubuntu2 amd64 [installed]
```
Find a package. See `man 8 apt-cache` and `man 7 regex`.
```
apt show neovim
```
Show package information.
```
apt install neovim
```
Install a package (or many)
```
apt reinstall neovim
```
Re-install a package

```
apt remove neovim
```
Remove a package, but can leave some files.
```
apt purge neovim
```
Purge system of all files that belongs to a package.


### Packages from `.deb` files

Some packages are distributed as `.deb` files.

```
apt install --fix-broken ./downloads/remarkable_1.95.deb 
```
Install package and dependencies.
