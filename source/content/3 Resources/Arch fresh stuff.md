---
created: 20220627-1127
tags:
  - Resources/Arch
---

# Arch fresh stuff
* check if base-devel packages are installed because they're used on every fuking build from the AUR
* Sometimes new installs have broken keyrings, you should update them first and then update packages. Like so:
> sudo pacman -S archlinux-keyring && sudo pacman -Syyu

  Not 5 minutes later I discovered someone using a command called `pacman-key --init` and it's apparently what I needed all along XD


### Install paru

[Github Repo](https://github.com/Morganamilo/paru)
``` bash
sudo pacman -S --needed base-devel
git clone https://aur.archlinux.org/paru.git
cd paru
makepkg -si
```
