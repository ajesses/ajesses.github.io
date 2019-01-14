---
title: linux设置定时任务之crontab
date: 2018-12-28 14:10:40
categories:
- Linux
tags:
- Linux
---

#### 安装

```shell
# 查看是否安装
$ rpm -qa crontab

$ yum -y install crontabs
```

#### 启动

```shell
$ ps -ef | grep cron

$ service crond start # 启动服务 
$ service crond stop # 关闭服务 
$ service crond restart # 重启服务 
$ service crond reload # 重新载入配置

$ service crond status # 查看服务状态
```
查看crontab服务是否已设置为开机启动，执行命令：`ntsysv`
或者执行`chkconfig –level 35 crond on`

- 若未找到`ntsysv`,则安装`yum -y install setuptool ntsysv`

#### 添加调度任务

```shell
# 编辑文件
$ vim /etc/crontab

# 列出当前的所有调度任务 
$ crontab -l

# 删除所有任务调度工作 
$ crontab -r 
```
> 注：你可以在`/var/spool/mail/root`中查看相应信息

格式描述：**minute hour day month dayofweek command**

- **minute**：从0到59的整数

- **hour**：从0到23的整数

- **day**：从1到31的整数 (必须是指定月份的有效日期)

- **month**：从1到12的整数 (或如Jan或Feb简写的月份)

- **dayofweek**：从0到7的整数，0或7用来描述周日 (或用Sun或Mon简写来表示)

- **command**：需要执行的命令(可用`as ls /proc >> /tmp/proc`或 执行自定义脚本的命令)

- 整数间的连字号`(-)`表示整数列，例如**1-4**意思是整数**1,2,3,4**

- 指定数值由逗号分开。如：**3,4,6,8**表示这四个指定整数。

- 符号`/`指定步进设置。`/<interger>`表示步进值。如**0-59/2**定义每两分钟执行一次。步进值也可用星号表示。如**/3**用来运行每三个月份运行指定任务

- 以`#`开头的为注释行,不会被执行

#### 配置目录

- **cron.daily**：是每天执行一次的job

- **cron.weekly**：是每个星期执行一次的job

- **cron.monthly**：是每月执行一次的job

- **cron.hourly**：是每个小时执行一次的job

- **cron.d**：是系统自动定期需要做的任务

- **crontab**：是设定定时任务执行文件

- **cron.deny**：文件就是用于控制不让哪些用户使用Crontab的功能

#### crontab-ui 可视化界面

- 安装`npm install -g crontab-ui`
- 启动`crontab-ui`
- 指定端口启动，远程访问`HOST=0.0.0.0 PORT=9000 crontab-ui`

#### 参考
* 参考1：https://www.linuxidc.com/Linux/2018-11/155189.html
* 参考2：https://blog.csdn.net/qq_39131177/article/details/79051711
* 参考3：https://zhuanlan.zhihu.com/p/45998227