---
layout: post
title: Mount Disk of iSCSI which in FreeNAS
---

First, install FreeNAS on a server and finish configurations on the web, like storage, sharing and service and so on.

Second, install `open-iscsi` on a target machine(maybe a client or a server)
> http://www.linuxdiyf.com/linux/31462.html

Third, partition, if small than 2TB -> fdisk, or if larger than 2TB -> gpart

Fourth, mount this disk

Fifth, auto mount it on startup.

