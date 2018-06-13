---
layout: post
title: FreeBSD
---

FreeBSD System Only

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
