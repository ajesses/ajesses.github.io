---
title: pm2使用
date: 2018-07-31 19:11:39
categories:
- Node
tags: 
- Node 
- Pm2
---
#### 安装
```
npm install pm2 -g
```

#### web查看
```
npm install pm2-web -g
```

#### pm2使用
```
pm2 start [filename].js    运行一个js文件
```
```
pm2 start npm --watch --name [aliasname] -- run start    运行node项目(npm run dev)
```
```
pm2 list    查看已启用项目
```
```
pm2 restart [Name]    重启
pm2 restart all       重启所有进程
pm2 reload all        0秒停机重载进程 [用于 NETWORKED 进程]
```
```
pm2 stop [Name]       停止
pm2 stop all          停止所有进程
```
```
pm2 delete [Name]    杀死项目
pm2 delete all       杀死全部进程
```
```
pm2 logs    显示所有进程日志
```
```
pm2 monit   监视每个node进程的CPU和内存的使用情况
```

#### pm2 logs日志存放位置（linux-centos）
```
cd /root/.pm2/logs/
```

**注意：若pm2启动express程序一直重启，可能是--watch的问题**