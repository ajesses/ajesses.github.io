---
title: linux常用命令
date: 2018-07-30 18:13:12
categories:
- Linux
tags:
- Linux
---
### 常用文件命令
#### linux重启
- **shutdown**
- **halt**

####  id：查看登录用户信息

#### 改密
- **passwd**

#### 创建目录：mkdir 
- **-p：**递归创建文件夹

#### 切换目录：cd
- **cd ~**与 **cd：**进入家目录
- **cd -：**进入上次目录
- **cd ..：**进入上一级目录
- **cd .：**进入当前目录

#### 删除文件：rm
- **rmdir：**不常用
- **rm -r：**会询问是否删除
- **rm -rf：**强制删除

#### 剪切文件和改名：mv

#### 复制命令：cp
- **-r：**复制目录
- **-p：**连带文件属性复制
- **-d：**若源文件是链接文件，则复制链接属性
- **-a：**相当于 **-pdr**

#### 显示当前路径：pwd
 - print working directory

#### 查询目录中的内容：ls
- **-a：**显示所有文件
- **-l：**显示文件详细信息，可以用 ll 表示
- **-d：**查看目录属性，目录本身
- **-h：**人性化显示文件大小
- **-i：**显示inode

#### 链接命令：ln
- **-a：**创建软链接（一定要写绝对路径）
**注：硬链接其实是同一个文件**

#### -rw-r--r--：
- **-：**代表文件
- **d：**代表目录
- **l：**代表软链接文件

| rw-          | r--          | r--|
| --------   | -----:  | :----:  |
|u所有者      | g所属组      | o其他人|

#### 三种权限：
- **r：**读
- **w：**写
- **x：**执行

#### 常用目录中：
 - **/：**根目录
 - **/bin、/sbin：**命令保存目录
 - **/usr：**系统软件资源目录
 - **/usr/bin：**普通用户系统命令
 - **/usr/sbin：**超级用户系统命令
 - **/boot：**启动目录
 - **/dev：**硬件目录
 - **/etc：**系统默认配置文件
 - **/home：**普通用户
 - **/root：**超级用户
 - **/lib：**函数库
 - **/media、/mnt、/misc：**空目录（用于挂外接设备等）
 - **/sys、/proc：**不能操作，保存内存数据
 - **/tmp：**临时目录
 - **/var：**系统相关文档

### 常用系统命令
#### 查看linux的CPU
```shell
$ cat /proc/cpuinfo | grep 'model name' |uniq
```

#### 查看CPU使用情况
```shell
$ top -bn 1 -i -c
$ top
```

#### 检查安装有没成功
- 例子
```shell
$ rpm -qa lrzsz
```

#### 查看ip
```shell
$ ip a
```

#### 查看启动
```shell
$ ps -aux |grep nginx
```

#### 查看文件容量和占用
```shell
$ df -h /opt
```

#### 查看hostname
```shell
$ uname -a
```

#### 切换用户
```shell
$ su root
```

#### 帮助命令
```shell
$ man -f [命令名]
$ man [级别] [命令名]
```

#### 查看网段和路由
```shell
$ netstat -rn  或者  netstat -r -anv  或者 route
```

#### 查看端口占用
```shell
$ netstat -luntp|grep 443
```

#### 查看linux外网IP
```shell
$ curl icanhazip.com
$ curl ifconfig.me
$ curl curlmyip.com
$ curl ip.appspot.com
$ curl ipinfo.io/ip
$ curl ipecho.net/plain
$ curl www.trackip.net/i
```

#### 查看当前用户名
```shell
$ users
$ whoami
$ id -un
$ printenv USER
<!-- 增加用户 -->
$ useradd [用户名]
$ passwd [用户名]
```

#### 查看环境变量
```shell
$ env
$ printenv [环境名]   // 可以打印出env的参数
```

#### 配置静态IP
```shell
$ cd /etc/sysconfig/network-scripts/
vim [配置文件名]
```

#### 系统安装时centos默认的发行版本信息
```shell
$ uname -a

$ cat /proc/version

$ cat /etc/redhat-release

<!-- 查看当前内核版本 -->
$ uname -r

$ uname -s
$ uname -m
```

#### 查看包是否安装
```shell
$ rpm -qa|grep [包名]

```