---
layout: post
title: WorkEnv Manjaro Rebuild
---

This is a record about how to configure a Linux environment for work after getting a whole new PC.  
And this post is based on Manjaro i3-wm.

Here we go!


## Catalogue
---
- Basic Configurations
  - [SSH Key](#ssh-key)
  - [zsh](#zsh)
  - [vim](#vim)
  - [Input method](#input-method)
  - [MultiDisplay](#multidisplay)
- Applications
  - [Firefox](#firefox)
  - [PyCharm Pro](#pycharm-pro)
  - [Franz](#franz)
  - [ThunderBird](#thunderbird)
  - [Typora](#typora)
  - [Remmina](#remmina)
  - [MQTTfx](#mqttfx)
  - [VirtualBox](#virtualbox)
  - [virt-manager](#virt-manager)
  - [LibreOffice](#libreoffice)
  - [XMind](#xmind)
- Backup
  - [timeshift](#timeshift)


## Basic configuration
---
### profile
- Configure the default editor and web browser
  ```shell
  vi ~/.profile
  ```
  > export EDITOR=/usr/bin/vim  
  > export BROWSER=/usr/bin/firefox


### zsh
- Generate SSH key if needed
  ```shell
  ssh-keygen -t rsa -b 4096
  ```
- Change `bash` to `zsh`, **WITHOUT** `sudo`. If it is after `sudo`, it changed shell of root user, not current user.
  ```shell
  chsh -s $(which zsh)
  ```

- Install oh-my-zsh
  ```shell
  sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
  ```

- Install `z`
  ```shell
  git clone https://github.com/rupa/z.git
  ```
  Add `. ~/path/to/z/z.sh` into `~/.zshrc`


### Vim
- Get ready a `.vimrc`  
  TODO: make a share link.

- Install Vundle.vim
  ```shell
  git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
  ```

- Open a file with `vim` and install plugins

  > :PluginInstall


### Input method
- fcitx-sogoupinyin
  ```shell
  yaourt -S fcitx fcitx-configtool fcitx-sogoupinyin
  ```
- If there was a error like: `unable to satisfy dependency 'libidn11' required by fcitx-sogoupinyin`  
  Refer to this post and fix it.
  > https://www.cnblogs.com/apocelipes/p/9702599.html  
  > 更新：Manjaro 18.0rc1及更新版本不再需要本文的操作，可直接成功安装sogoupinyin

- Add content below into `~/.xprofile` or `~/.extend.xprofile`, if not exists, create it.
  > export GTK_IM_MODULE=fcitx  
  > export QT_IM_MODULE=fcitx  
  > export XMODIFIERS="@im=fcitx"  
  > \# Below is a bug fix, maybe try to delete this line next version
  > fcitx -d -r --enable sogou-qimpanel

- Bug fix
  Unable to start? Try `rm -rf ~/.sogouinput`
  Still not working? Try `rm -rf ~/.sogouinput ~/.config/SogouPY*` and re-login.

- Find and install a plugin of `vim-fcitx` in the packmanager  
  Like always typing English in normal mode, but Chinese in insert mode.


### MultiDisplay
Actually, it is not really need multiDiskplay, because thereis no desktop in FreeBSD
and there are multiDesktop in Manjaro and macOS
- Manjaro i3wm 17.1.5
  ```shell
  xrandr --auto --output DP1 --mode 1920x1080 --right-of HDMI1
  ```
  
[Back to catalogue](#catalogue)


## Applications
---
### Firefox
```shell
yaourt -S firefox
```

[Back to catalogue](#catalogue)


### PyCharm Pro
- Get activation code of PyCharm Pro at `https://blog.csdn.net/u014044812/article/details/78727496`
- 将.idea目录加入ignore清单：
  ```shell
  echo '.idea' >> .gitignore
  git rm --cached -r .idea
  git add .gitignore
  git commit -m '(gitignore commit and remove .idea)'
  git push
  ```

[Back to catalogue](#catalogue)


### Franz
```shell
yaourt -S franz-bin
```


### ThunderBird
```shell
yaourt -S thunderbird
```



### Typora

```shell
yaourt -S typora
```



### Remmina

```shell
yaourt -S remmina
```


### MQTTfx
MQTT.fx is a nice tool to debug.  
But it may be stopped by an error: `ERROR: options array contains unknown option '!upx'`

To fix this bug:
```shell
# NOT with sudo
yaourt -S mqttfx-bin
```
When pop a prompt, edit the BUILD file and remove the `'!upx'`  

After installation, `mod + d` could not involed the `/opt/MQTTfx/MQTTfx`  
```shell
ll /usr/bin/mqttfx
```
> lrwxrwxrwx 1 root root 18 Aug 22 16:36 /usr/bin/mqttfx -> /opt/mqttfx/mqttfx

I just had a try, but it worked:
```shell
sudo rm /usr/bin/mqttfx
sudo ln -s /opt/MQTTfx/MQTTfx /usr/bin/mqttfx

ll /usr/bin/mqttfx 
```
> lrwxrwxrwx 1 root root 18 Aug 22 18:49 /usr/bin/mqttfx -> /opt/MQTTfx/MQTTfx

[Back to catalogue](#catalogue)


### VirtualBox
VirtualBox
it will show something like this Linux user 4.6.0-1-MANJARO #1 SMP PREEMPT Mon May 16 02:44:59 2016 x86_64 GNU/Linux
In bold is your kernel version, so install the virtualbox host modules for your kernel number replacing 46 with what your output showed from the above.
sudo pacman -S linux46-virtualbox-host-modules
Now load your virtualbox module
sudo /sbin/rcvboxdrv setup
Virtualbox should run normally now - if not, use pamac and uninstall anything related to virtualbox then just install the 'virtualbox' package and it will do the above for you if you tell it the kernel version you are using
http://idea.iteblog.com/key.php

[Back to catalogue](#catalogue)


### virt-manager
Maybe there is a bug of virt-manager in Manjaro-i3wm that 'You need to install openssh-askpass or similar to connect to this host'  
So resolvation is `sudo virt-manager –no-fork`

This worked, but have to open a terminal to run command as above.

And then another post get this problem done:
> If you use gnome-shell, install the package x11-ssh-askpass instead of openssh-askpass and the problem is solved

```shell
yaourt -S x11-ssh-askpass
```
Even still a little ugly, but it works.

[Back to catalogue](#catalogue)


### LibreOffice
```shell
yaourt -S libreoffice
```

[Back to catalogue](#catalogue)


### XMind
```shell
yaourt -S xmind
```

[Back to catalogue](#catalogue)


## Backup
---
### timeshift
```shell
yaourt -S timeshift
```

[Back to catalogue](#catalogue)

