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
