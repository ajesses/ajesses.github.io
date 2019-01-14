---
title: linux设置禁用外网，只连局域网
date: 2018-11-02 14:51:47
categories:
- Linux
tags:
- Linux
---

### 如何让电脑不能上网但又不影响局域网的连接呢（linux）?

#### 修改配置
```
 vim /etc/sysconfig/network-scripts/ifcfg-enp0s25
```

![network配置](/images/network/network.png)
把 **GATEWAY=192.168.0.1**和 **DNS**的配置删除

```
 vim /etc/resolv.conf
```
把nameserver的配置删除

#### 查看
```
 netstat -r
```

#### 重启网卡
```
service network restart
```