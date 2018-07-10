---
layout: post
title: Work Environment Rebuild
---

This is a record about how to configure a Linux environment for work after getting a whole new pc, NOT include macOSX.

## Basic configuration
---
### SSH Key
- Generate SSH key if needed
  ```shell
  ssh-keygen -t rsa -b 4096
  ```


### Shell
- Change `bash` to `zsh`, without `sudo`. If it is after `sudo`, it changed shell of root user, not current user.
  ```shell
  chsh -s $(which zsh)
  ```

- Install oh-my-zsh
  ```shell
  sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
  ```

- Install `z`, follow the steps in README
  ```shell
  git clone git@github.com:rupa/z.git
  ```

### Vim
- Get ready a `.vimrc`  
  TODO: make a share link.
### Test
Test body
#### test
4level test text
- hoho
- HOHO

### Input method
- fcitx-sogoupinyin
  ```shell
  sudo pacman -S fcitx-im
  sudo pacman -S fcitx-configtool
  ```
#### 4Level
  - maybe need a long time

- Add content below into `~/.xprofile` or `~/.extend.xprofile`, if not exists, create.
  > export GTK_IM_MODULE=fcitx
  > export QT_IM_MODULE=fcitx
  > export XMODIFIERS="@im=fcitx"
#### 4level
- 1
- 2

### MultiDisplay
Actually, it is not really need multiDiskplay, because thereis no desktop in FreeBSD
and there are multiDesktop in Manjaro and macOS
- Manjaro i3wm 17.1.5
  ```shell
  xrandr --auto --output DP1 --mode 1920x1080 --right-of HDMI1
  ```


## PyCharm Pro
---
### Installation
- PyCharm Pro
  `https://blog.csdn.net/u014044812/article/details/78727496`


### Configuration
- 将.idea目录加入ignore清单：
  ```shell
  echo '.idea' >> .gitignore
  git rm --cached -r .idea
  git add .gitignore
  git commit -m '(gitignore commit and remove .idea)'
  git push
  ```


## VirtualBox
---
VirtualBox
it will show something like this Linux user 4.6.0-1-MANJARO #1 SMP PREEMPT Mon May 16 02:44:59 2016 x86_64 GNU/Linux
In bold is your kernel version, so install the virtualbox host modules for your kernel number replacing 46 with what your output showed from the above.
sudo pacman -S linux46-virtualbox-host-modules
Now load your virtualbox module
sudo /sbin/rcvboxdrv setup
Virtualbox should run normally now - if not, use pamac and uninstall anything related to virtualbox then just install the 'virtualbox' package and it will do the above for you if you tell it the kernel version you are using
http://idea.iteblog.com/key.php

