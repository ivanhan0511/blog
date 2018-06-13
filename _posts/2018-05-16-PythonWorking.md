---
layout: default
title: RD and Testing Env
---

# RD and Testing Env
## Work in Manjaro, FreeBSD and macOSX



### Catalogue

- Introduction


- Basic Configuration
  - Input method
  - oh-my-zsh
  - z
  - vim
  - MultiDisplay
  - VirtualBox etc.

- Development
  - Python3
  - PostgreSQL
  - PyCharm
  - DataGrip








### Introduction

---

I have RD project both in two environments, and the resolution is as below:

#### Work Env

- Server: Ubuntu and FreeBSD in normal server
- Client: Manjaro i3wm in normal pc

#### Home Env

- Both server and client are in MacBookPro

#### Software

- Python + Django + PostgreSQL + MQTT(mosquitto)


  

  


### Basic Configuration
---
#### Basic

- Manjaro i3wm 17.0
- macOS 10.13
- FreeBSD 12.0



#### Input method

- Manjaro i3wm 17.0
  - 安装搜狗输入法及图形化配置工具
    ```shell
    sudo pacman -S fcitx-im
    sudo pacman -S fcitx-configtool
    ```
  - 在`~/.xprofile`或`~/.extend.xprofile`文件里面添加下面三行
    > export GTK_IM_MODULE=fcitx
    > export QT_IM_MODULE=fcitx
    > export XMODIFIERS="@im=fcitx"



- macOS
- FreeBSD



#### oh-my-zsh
https://github.com/robbyrussell/oh-my-zsh
相关文档http://macshuo.com/?p=676




#### z
https://github.com/rupa/z


#### MultiDisplay
Actually, it is not really need multiDiskplay, because thereis no desktop in FreeBSD 
and there are multiDesktop in Manjaro and macOS
- Manjaro i3wm 17

  ```shell
  xrandr --auto --output DP1 --mode 1920x1080 --right-of HDMI1
  ```



#### VirtualBox

VirtualBox
it will show something like this Linux user 4.6.0-1-MANJARO #1 SMP PREEMPT Mon May 16 02:44:59 2016 x86_64 GNU/Linux
In bold is your kernel version, so install the virtualbox host modules for your kernel number replacing 46 with what your output showed from the above.
sudo pacman -S linux46-virtualbox-host-modules
Now load your virtualbox module
sudo /sbin/rcvboxdrv setup
Virtualbox should run normally now - if not, use pamac and uninstall anything related to virtualbox then just install the 'virtualbox' package and it will do the above for you if you tell it the kernel version you are using
http://idea.iteblog.com/key.php

  

  


#### FreeBSD System Only

- Install FreeBSD (Until now, Sep 08, 2017, FreeBSD12.0 armv8)
- Enable ssh for remote login
- First update `portsnap fetch extract`
- Ports install tmux
- Ports install axel and add `/etc/make.conf`
  > FETCH_CMD=axel
  > FETCH_BEFORE_ARGS= -n 10 -a
  > FETCH_AFTER_ARGS=
  > DISABLE_SIZE=yes
  > ~~MASTER_SITE_OVERRIDE?=\~~
  > ~~http://ports.hshh.org/${DIST_SUBDIR}/\~~
  > ~~http://ports.cn.freebsd.org/${DIST_SUBDIR}/\~~
  > ~~ftp://ftp.freeBSDchina.org/pub/FreeBSD/ports/distfiles/${DIST_SUBDIR}/~~
  > ~~MASTER_SITE_OVERRIDE?=${MASTER_SITE_BACKUP}~~
- Ports install Python3.6.2 and pip3
  ```shell
  python3.6 -m ensurepip
  pip3 -h
  ```
- Ports install mosquitto and configure broker

- Ports install vim, git and Vundle
- Change default shell to zsh and install OhMyZsh
- ~~Ports install nginx~~
  So far, use Django webserver is satisfied, no need Nginx or Apache






### Development 

---

#### 安装策略

- macOS

  采用macports机制，都在`/opt/`目录下，对系统原有各种库没有影响

- FreeBSD

  port编译安装

- Manjaro

  yaourt安装





#### Python3





#### PostgreSQL

mariadb100-server is marked broken in FreeBSD arm 12.0
Both mysql and mariadb are **sucks**, so go into PostgreSQL
The difference between these 3 systems is the path.
As example of FreeBSD

```shell
su root
ports install postgresql10-server
pw user add postgres
chown postgres:postgres /var/db/postgres/data

su - postgres
initdb -D /var/db/postgres/data
postgres -D /var/db/postgres/data &
vi /var/db/postgres/data/pg_hba.conf
```
> host    all             all              0.0.0.0/0              md5

```shell
vi /var/db/postgres/data96/postgresql.conf
```
> listen_addresses = '\*'

Export and import database like below
```shell
pg_dump -U USERNAME DBNAME > dbexport.pgsql
#pg_dump -U USERNAME DBNAME -N topology -T spatial_ref_sys > dbexport.pgsql  # If with restricted access permissions
psql -U USERNAME DBNAME < dbexport.pgsql
```

Python __private(self)的轧压
'http://greybeard.iteye.com/blog/1355216'


- create database of postgresql
- PyCharm: python3 manage.py migrate
- python3 manage.py createsuperuser


>>> for i in enumerate('b 2:6 rwm'):
...     print(i)
...
(0, 'b')
(1, ' ')
(2, '2')
(3, ':')
(4, '6')
(5, ' ')
(6, 'r')
(7, 'w')
(8, 'm')



