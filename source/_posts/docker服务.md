---
title: docker服务
date: 2018-12-20 16:41:12
categories:
- Docker
tags:
- Docker
---

#### 定义
一项服务仅运行一个镜像，但它会编制镜像的运行方式 - 它应使用的端口、容器的多少个从节点应运行才能使服务的容量满足其需求等。扩展服务将更改运行该软件的容器实例数，并将多个计算资源分配给进程中的服务。
 Docker 平台定义、运行和扩展服务 – 只需编写一个 `docker-compose.yml` 文件即可

 #### docker-compose.yml
```yaml
version: '3'

services:
  web:
    # 将 username/repo:tag 替换为您的名称和镜像详细信息
    image: username/repo:tag
    deploy:
      replicas: 5
      resources:
        limits:
          cpus: "0.1"
          memory: 50M
      restart_policy:
        condition: on-failure
    ports:
      - "80:80"
    networks:
      - webnet
networks:
  webnet:
```
此 `docker-compose.yml` 文件会告诉 Docker 执行以下操作：

- 从镜像库中拉取我们上传的镜像。

- 将该镜像的五个实例作为服务 web 运行，并将每个实例限制为最多使用 10% 的 CPU（在所有核心中）以及 50MB RAM。

- 如果某个容器发生故障，立即重启容器。

- 将主机上的端口 80 映射到 web 的端口 80。

- 指示 web 容器通过负载均衡的网络 webnet 共享端口 80。（在内部，容器自身将在临时端口发布到 web 的端口 80。）

- 使用默认设置定义 webnet 网络（此为负载均衡的 overlay 网络）。

#### 运行新的负载均衡的应用

需要先运行
```shell
$ docker swarm init
```
> 如果未运行 `docker swarm init`，您将收到错误消息: 此节点不是 swarm 管理节点

再运行
> 您必须为应用指定一个名称。在此处该名称设置为 **getstartedlab**
```shell
$ docker stack deploy -c docker-compose.yml getstartedlab
```

查看您刚才启动的五个容器的列表
```shell
$ docker stack ps getstartedlab
```

在浏览器中转至该 URL 并多次点击“刷新”
> 将看到容器 ID 更改，从而说明负载均衡；借助每项请求，将以循环方式选择五个从节点之一做出响应

相关命令
```shell
# 列出此 $ Docker 主机上所有正在运行的应用
$ docker stack ls
# 运行指定的 Compose 文件           
$ docker stack deploy -c <composefile> <appname>
# 列出与应用关联的服务
$ docker stack services <appname>
# 列出与应用关联的正在运行的容器
$ docker stack ps <appname>
# 清除应用
$ docker stack rm <appname>
```

摘自[docker中文网]**https://docs.docker-cn.com/get-started/part3**