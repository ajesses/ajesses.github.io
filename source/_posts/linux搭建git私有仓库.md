---
title: linux搭建git私有仓库
date: 2018-08-13 11:28:05
categories:
- Git
- Linux
tags:
- Git
- Linux
---
#### 查看ssh版本
```
ssh -V
```
#### 请确保您切换到了root账户
```
su root
```

#### 安装git
```
yum -y install git
git --version                   查看git安装成功
cd /home && ls -al              查看git安装成功
```

#### 添加git账户和设置密码
```
adduser git
passwd git                      修改密码
```

#### 设置ssh访问
```
su git                          切换git账户
cd /home/git

mkdir .ssh                      创建.ssh配置

cd /home/git/.ssh               进入刚创建的.ssh目录
touch authorized_keys           创建authorized_keys文件

chmod 700 /home/git/.ssh/       设置权限(必须)
chmod 600 /home/git/.ssh/authorized_keys
```

#### 创建客户端的ssh私钥和公钥
1. 检查是否已创建(.ssh文件)
```
Windows系统上目录：C:\Users\用户名
Linux系统上目录：/home/用户名
Mac系统上目录：/Users/用户名

此文件：id_rsa.pub即私钥
```
2. 没有就创建
```
ssh-keygen -t rsa       默认回车
```

#### 拷贝私钥到git的服务器
1. 上传
```
cd /home/git/.ssh
rz
ls -al     查看上传成功
```
2. 上传的文件内容拷贝到authorized_keys
```
cat id_rsa.pub >> authorized_keys
```

#### 客户端检查
```
ssh git@设置的linux的ip地址
第一次连接有警告，输入yes继续即可。如果可以连接上，那么ssh配置已经成功 
```

#### 进行测试
##### 服务端创建git仓库
```
su git

cd /home/git    在用户主目录下创建 [文件名].git仓库

mkdir [文件名].git && cd [文件名].git

git init --bare         初始化git仓库

输出内容，提示成功
```

##### 客户端连接
```
git init

添加内容

git add .

git commit -m "first commit"

！把当前仓库跟远程仓库添加映射
git remote add origin git@[linux IP]:[文件名].git

！把当前仓库push到远程仓库
git push -u origin master
```

#### 安全设置(禁止客户端shell登录)
```
su git
mkdir /home/git/git-shell-commands  (必须)

su root
vim /etc/passwd
```
**找到这句：可以通过 vim的正则搜索,命名模式下:/git:x**
```
注释
git:x:1000:1000::/home/git:/bin/bash
修改为
git:x:1000:1000::/home/git:/bin/git-shell
```