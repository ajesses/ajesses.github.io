---
title: linux安装redis
date: 2018-07-31 15:33:57
categories:
- Linux
tags:
- Linux
- redis
---
#### 安装依赖
```
yum -y install gcc gcc-c++
yum -y install wget
```

#### 安装步骤
1.
```
wget http://download.redis.io/releases/redis-3.2.9.tar.gz
```
2.
```
tar xzf redis-3.2.9.tar.gz
```
3.
```
cd redis-redis-3.2.9
```
4.
```
make
```

#### 远程连接
1. 修改配置(安装目录下)
    ```
    vi redis.conf
    ```
     a. 把bind 127.0.0.1 ::1这一行注释掉
     b. protected-mode 要设置成no
     c. 启动的时候，需要指定redis.conf 文件
2. 关闭防火墙firewall

#### 启动redis
```
src/redis-server redis.conf
```
#### redis后台启动
```
进入redis目录
vim redis.conf
找到daemonize no
改为daemonize yes
重启
```

#### redis查看版本
```
./redis-cli -h 127.0.0.1 info | grep 'redis_version'  
```

#### 出现问题
##### 关闭防火墙
```
service firewalld stop      关闭firewall
systemctl disable firewalld.service    禁止firewall开机启动
```