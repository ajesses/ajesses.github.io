---
title: docker常用工具
date: 2018-12-20 19:22:45
categories:
- Docker
tags:
- Docker
---

#### docker-compose安装

https://docs.docker.com/compose/install/#install-compose

##### 安装
例如：
```shell
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.23.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

$ sudo chmod +x /usr/local/bin/docker-compose

$ docker-compose --version
```

#### docker machine

https://docs.docker-cn.com/machine/install-machine/#installing-machine-directly

##### 安装

```shell
$ curl -L https://github.com/docker/machine/releases/download/v0.12.1/docker-machine-`uname -s`-`uname -m` >/tmp/docker-machine &&
chmod +x /tmp/docker-machine &&
sudo cp /tmp/docker-machine /usr/local/bin/docker-machine
```
查看版本
```shell
$ docker-machine version
docker-machine version 0.12.1, build c8b17e8
```

##### 创建
运行`docker-machine`,添加驱动`--driver virtualbox`，如果是第一次创建，则加上参数`default`，否则添加`name`
```shell
# 查看
$ docker-machine ls
# 创建
$ docker-machine create --driver virtualbox default

$ docker-machine env default
```