---
title: 一台同时连接github和码云
date: 2018-08-14 15:54:56
categories:
- Git
- SSH
tags:
- Git
- SSH
---
#### 生成ssh
```
$ cd ..\.ssh\         windows上的.ssh一般在用户目录下
$ ssh-keygen -t rsa -C "邮箱名"

生成2个：github_rsa和gitee_rsa(默认为id_rsa)
```
![ssh生成演示](/images/ssh/ssh-create.png)
这里，我已经生成过了，提示会覆盖
一般会要求设置密码（可以为空）

#### 新建config文件
```
$ touch config        (在.ssh文件夹里)
$ vim config
```
添加下列代码：
```
Host github.com
HostName github.com
IdentityFile ~/.ssh/github_rsa
  
Host gitee.com
HostName gitee.com
IdentityFile ~/.ssh/gitee_rsa
```

#### 把两个SSH key的密钥加入ssh 的 agent中去
```
$ ssh-add -D
$ ssh-add github_rsa
$ ssh-add gitee_rsa
```

若执行 **ssh-add -D** 是出现这个错误:**Could not open a connection to your authentication agent**，则先执行如下命令即可：**ssh-agent bash**

若执行 **git push origin master** 出现这个错误 **Permission denied(publickey).**，则执行 **ssh-add ~/.ssh/your_publickey**；若还出现 **Could not open a connection to your authentication agent.**，则执行 (eval `ssh-agent  -s`)，然后在执行 **ssh-add**

#### 测试连接
```
$ ssh -T git@github.com
$ ssh -T git@gitee.com
```