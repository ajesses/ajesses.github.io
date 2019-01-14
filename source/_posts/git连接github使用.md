---
title: git连接github使用
date: 2018-12-19 11:26:32
categories:
- Git
tags:
- Git
---
#### 注意
出现
```shell
$ git: 'credential-cache' is not a git command. See 'git --help'.
```

解决
**./git/config**里面添加

```config
[user]
    name = username
    email = username@gmail.com
[credential]
    helper = cache
```

执行
```shell
$ git config --global user.name "username"
$ git config --global user.email "username@gmail.com"

$ git config --global credential.helper wincred

```
