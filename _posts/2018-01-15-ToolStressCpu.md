---
layout: post
title: Pressure Testing
---

High privilege with `stres` and `nmon`

#### Installation
```shell
apt install stress
apt install nmon
```


### As below, just for reference
---
测试对U盘的读写速度，Ubuntu自带

```shell
hdparm -Tt /dev/sdb
```


温度测量

```shell
sudo apt install lm-sensors
sensors
```


UnixBench搜索网站，其中有下载，需要down到本地并编译安装

```shell
cd 
# 并不需要`configure`
make
# 也不需要`make install`
./Run
```

