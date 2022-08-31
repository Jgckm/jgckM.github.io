---
title: shell入门
abbrlink: 16d516d8
date: 2022-08-22 14:19:43
tags: 
  - Linux
  - Shell
cover:
categories:
   - Linux
---

> Shell 是一个用 C 语言编写的程序，它是用户使用 Linux 的桥梁。Shell 既是一种命令语言，又是一种程序设计语言。
>
> Shell 是指一种应用程序，这个应用程序提供了一个界面，用户通过这个界面访问操作系统内核的服务。
>
> Ken Thompson 的 sh 是第一种 Unix Shell，Windows Explorer 是一个典型的图形界面 Shell。

脚本以 {% label #!/bin/bash red%} 开头(指定解析器)

执行方式 

| 命令                             | 描述     |
| -------------------------------- | -------- |
| [bash/sh] [绝对路径或者相对路径] | 执行脚本 |



1. 采用 `bash` 或 `sh` 脚本的相对路径或者绝对路径(不用赋予脚本+x权限)

```
bash hello.sh
```

2. 直接写出相对路径或者是绝对路径(这种方式必须需要权限才可以)

```
/root/scripts/hello.sh
```

# 变量

## 常用系统变量

$HOME、$PWD、$SHELL、$USER等

如果想要看全局变量 

```
env

printenv

printenv USER # 获取 USER 全局变量

set # 包含了所有的全局变量
```

## 自定义变量

语法  

- 变量名=变量值 {% label 注意：=前后不能有空格 red%}
- 撤销变量 ：unset 变量名
- 声明静态变量(不可以改变) readonly 变量 ，{% label 注意不能 unset red%}

变量定义规则

- 变量名称可以由字母、数字、下划线组成，但是 {% label 不能以数字开头 green%}，{% label 环境变量建议大写 red%} 
