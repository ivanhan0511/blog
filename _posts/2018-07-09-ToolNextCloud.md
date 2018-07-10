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

### Configuration
```shell
sudo vi /var/snap/nextcloud/current/nextcloud/config/config.php
```
- Change data storage path if needed
  > 'datadirectory' => '/var/snap/nextcloud/common/nextcloud/data' 

- Change database service if needed
  > 'dbname' => 'nextcloud',
  > 'dbhost' => '192.168.1.xxx:/var/run/mysqld/mysqld.sock',
  > 'dbuser' => 'nextcloud',
  > 'dbpassword' => 'xxx',


## Checkout
---
- 查看进程：`ps aux | grep nextcloud`
- 停止服务：`sudo systemctl stop snap.nextcloud.xxx`，其中包含apache、mysql、php等服务
- 日志：
  ```shell
  cd /var/snap/nextcloud/current/apache/
  sudo ls logs/
  sudo cat logs/error_log
  ```


