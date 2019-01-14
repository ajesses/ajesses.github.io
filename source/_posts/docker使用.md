---
title: docker使用
date: 2018-12-18 19:18:58
categories:
- Docker
tags:
- Docker
---

#### 安装
http://www.runoob.com/docker/centos-docker-install.html

#### 常用命令
运行：**docker run [image]**

查看镜像：
```shell
$ docker images
$ docker images -a
```

当前正在运行的容器: **docker ps**

停止容器：**docker stop [containerId]**

例子:
```shell
# -p: 端口映射; -d: 直接返回，container作为守护进程运行
$ docker run -p [映射端口号]:80 -d nginx
```
从正在运行的 Docker 容器里面，将文件拷贝到本机，当前目录：**docker cp [文件名] [containerId]://[path路径]** .

移除image：**docker rmi [imageId]**

容器历史记录：**docker ps -a**

查看日志：**docker container logs**

移除容器历史记录：**docker rm [containerId]**

进入容器：**docker container exec -it [containerID] /bin/bash**

docker登录
```shell
# 使用您的 Docker 凭证登录此 CLI 会话
$ docker login
# 标记 <image> 以上传到镜像库
$ docker tag <image> username/repository:tag
# 将已标记的镜像上传到镜像库
$ docker push username/repository:tag
# 运行镜像库中的镜像
$ docker run username/repository:tag
```

![docker命令1](/images/docker/docker_01.png)
![docker命令2](/images/docker/docker_02.png)

Dockerfile使用

![dockerfile1](/images/docker/dockerfile_01.png)
![dockerfile2](/images/docker/dockerfile_02.png)
