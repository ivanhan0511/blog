---
layout: post
title: Pressure Testing
---

High privilege with `stress` and `nmon`
## stress
---
A greate tool.

### Installation
```shell
apt install stress
apt install nmon
```

### usage examples
`https://www.hi-linux.com/posts/59095.html`


## nmon
---
Something about nmon


## Others
---
### hdparm
测试对U盘的读写速度，Ubuntu自带

```shell
hdparm -Tt /dev/sdb
```

### lm-sensors
温度测量
```shell
sudo apt install lm-sensors
sensors
```

### unixbench
UnixBench搜索网站，其中有下载，需要down到本地并编译安装

```shell
cd 
# 并不需要`configure`
make
# 也不需要`make install`
./Run
```

