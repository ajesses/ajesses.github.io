---
title: linux常用依赖包
date: 2018-07-31 15:08:55
categories:
- Linux
tags:
- Linux
---
#### linux查看某命令在哪个依赖包中
```shell
$ yum search [命令名]
```
#### 查看端口使用
```shell
$ netstat -lunpt   查看
$ yum -y install net-tools   安装
```

#### 上传文件
```shell
$ rz -be    本地上传文件到服务器
$ sz [filename]     发送文件到本地
$ yum -y install lrzsz
```

#### wget
```shell
$ yum -y install wget
```

#### 解压命令
```shell
$ unzip [filename].zip
$ yum -y install zip unzip
```

#### 权限
```shell
$ chmod -R  777  [filename]
```

#### vim编辑器
```shell
$ yum -y install vim
```

#### ab测试工具
```shell
$ yum -y install httpd-tools
```

#### DNS 服务器软件
```shell
$ yum -y install bind
```

#### nslookup是常用来查询本机域名解析情况的命令
```shell
$ yum -y install bind-utils
```