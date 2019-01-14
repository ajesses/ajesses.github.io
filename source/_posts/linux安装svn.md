---
title: linux安装svn
date: 2018-11-02 14:17:15
categories:
- Linux
tags:
- Linux
- svn
---
#### 安装
- 检查安装
```
rpm -qa subversion
```

- 安装
```
 yum install httpd httpd-devel subversion mod_dav_svn mod_auth_mysql
```

- 验证安装
```
cd /etc/httpd/modules
ls | grep svn
mod_authz_svn.so
mod_dav_svn.so
```

- 查看版本
```
svnserve --version
```

#### 代码库创建
- 待写

#### 启动
```
svnserve -d -r /opt/svn/repositories
```

#### 查看进程
```
ps -ef|grep svn|grep -v grep

netstat -ln |grep 3690
```

**注意：linux重启后，svn需要重启才能用**
```
kill -9 [进程号]

svnserve -d -r [安装目录]  
```
**(到/usr/bin/目录下执行svnserve -d -r /home/svn/进行启动)**
