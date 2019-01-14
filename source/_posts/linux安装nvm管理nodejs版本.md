---
title: linux安装nvm管理nodejs版本
date: 2018-07-31 14:48:05
categories:
- Linux
- Node
tags:
- Linux
- nvm
---
#### curl方式
```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.1/install.sh | bash
```

#### 问题
### 远程连接需，重启xshell
### 依旧提示找不到nvm命令，那么请使用source命令
```
source ~/.bashrc
```

#### 查看可安装node版本
```
nvm ls-remote
```

#### 安装node版本
```
nvm install v8.9.4
```

#### 切换node版本
```
nvm use v8.9.4
```

#### 查看已安装node版本
```
nvm list
```