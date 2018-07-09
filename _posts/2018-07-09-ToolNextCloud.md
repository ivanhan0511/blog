---
layout: post
title: NextCloud
---

High privilege with `stres` and `nmon`

## Installation
---
### Install
```shell
sudo apt update
sudo snap install nextcloud
```

### Activate
Open a browser of `http://host_ip` and set a username and password.
Wait for a moment and it is done.

### Enable https
```shell
sudo nextcloud.enable-https self-signed
```

### Change data path if needed
```shell
cd /var/snap/nextcloud/current/nextcloud/config/
vi config.php
```
>  'datadirectory' => '/var/snap/nextcloud/common/nextcloud/data' 




## Checkout
---
- 查看进程：`ps aux | grep nextcloud`

- 停止服务：`sudo systemctl stop snap.nextcloud.xxx`，其中包含apache、mysql、php等服务


