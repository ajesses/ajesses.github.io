---
title: nginx
date: 2018-07-30 18:04:40
categories:
- Linux
tags:
- Nginx 
- Linux
---
### 四项确认
1. 可联网
2. **yum**可使用
3. **iptables**关闭
    **iptables -L：**查看
    **iptables -F：**关闭
    **iptables -t nat -L**
   **iptables -t nat -F**

**注意：**
**centos从7开始默认用的是firewalld，这个是基于iptables的，虽然有iptables的核心****但是iptables的服务是没安装的。所以你只要停止firewalld服务即可**
```
systemctl status firewalld.service       查看service状态
    systemctl stop firewalld.service        关闭此服务
    systemctl disable firewalld.service     移除此服务
```

4. **getenforce**关闭
    **getenforce：**查看
    **setenforce 0：**切换状态

### 安装必要依赖
```
yum -y install gcc gcc-c++ autoconf pcre pcre-devel make automake
```
```
yum -y install wget httpd-tools vim
```
#### 初始化目录(在/opt目录下)
```
mkdir app backup download logs work
```
- **app：**存放代码应用
- **backup：**存放备份文件
- **download：**相关下载文件
- **logs：**日志文件
- **work：**工作文件

### 安装nginx
#### 创建文件
```
vi /etc/yum.repos.d/nginx.repo
```
#### 添加
```
[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/centos/7/$basearch/
gpgcheck=0
enabled=1
```

#### 列出版本号
```
yum list |grep nginx
```
#### 安装
```
yum -y install nginx
```
#### 查看
```
nginx -v
```
```
nginx -V
```

#### nginx测试配置文件
```
/usr/sbin/nginx -t

nginx -t -c /etc/nginx/nginx.conf
```

#### 查看进程
```
ps aux|grep nginx
```

#### 启动 / 停止 nginx
```
cd /usr/sbin/
./nginx
./nginx -s stop
./nginx -s quit
./nginx -s reload
```

#### nginx重启
```
/usr/sbin/nginx -s reload
```

#### nginx重载配置文件
```
nginx -s reload -c /etc/nginx/nginx.conf
```

#### nginx初始化静态文件目录
```
/usr/share/nginx/html
```

#### https配置
- openssl证书生成(个人-自签名)
```
openssl genrsa -idea -out jesse.key 1024

openssl req -new -key jesse.key -out jesse.csr

openssl x509 -req -days 3650 -in jesse.csr -signkey jesse.key -out jesse.crt
```