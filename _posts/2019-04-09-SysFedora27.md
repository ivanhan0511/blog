---
layout: post
title: After Installed Fedora Server
---

Take some records about what to do after installation of Fedora Server 25


- Disable SeLinux
  ```shell
  getenforce  # 查看SeLinux状态
  vi /etc/selinux/config
  ```
  > SELINUX=disabled

- Remove firewalld
  ```shell
  systemctl status firewalld
  systemctl stop firewalld
  dnf remove firewalld
  ```

- Reboot for effect
  ```shell
  reboot
  ```

- Update yum repository
  https://blog.csdn.net/javafoam/article/details/78992486

  ```shell
  sudo dnf install yum-fastestmirror
  cd /etc/yum.repos.d
  # AliYun
  sudo wget -O /etc/yum.repos.d/fedora.repo http://mirrors.aliyun.com/repo/fedora.repo
  sudo wget -O /etc/yum.repos.d/fedora-updates.repo http://mirrors.aliyun.com/repo/fedora-updates.repo
  yum makecache
  ```
