---
layout: post
title: NextCloud
---

A new type of installing nextcloud on Ubuntu Server 18.04.

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


### Import external DB
Mysql Index column size too large错误解决方案

mysql在执行脚本时，报出了以下错误：
> index column size too large. the maximum column size is 767 bytes

解决方案：
- 对数据库进行设置
  ```shell
  set global innodb_file_format = BARRACUDA;
  set global innodb_large_prefix = ON;
  ```
- 对脚本进行修改，添加`ROW_FORMAT=DYNAMIC`
> create table test (........) ENGINE=InnoDB DEFAULT CHARSET=utf8 ROW_FORMAT=DYNAMIC;


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

