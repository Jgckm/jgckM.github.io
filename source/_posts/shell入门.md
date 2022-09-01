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
- 声明静态变量(不可以改变) readonly 变量 ，{% label 注意不能 unset 撤销 red%}

变量定义规则

- 变量名称可以由字母、数字、下划线组成，但是 {% label 不能以数字开头 green%}，{% label 环境变量建议大写 red%} 
- 等号两侧不能有空格
- 在 bash 中，变量默认都是字符串类型，无法直接进行数值运算 `a =$[2+1]`或`a=$((2+1))`
- 变量的值如果有空格，需要使 {% label 用双引号或单引号 green%}
- 双引号可以解析里面的$变量
- 单引号直接输入

# 特殊变量

## `$n`  

`$n` n 为数字，$0 为该脚本的名称，$1-$9表示一到九个参数，十以上的参数，需要用大括号包含，如${10}

```bash
#!/bin/bash
# parameter.sh
echo ============$0===============
echo script name: $0
echo parameter1: $1
echo parameter2: $2

=================运行结果======================
./parameter.sh abc def
============./parameter.sh===============
script name: ./parameter.sh
parameter1: abc
parameter2: def

```



## `$#`

输出 输入参数个数

```bash
#!/bin/bash
echo '============$0===============''
echo script name: $0
echo parameter1: $1
echo parameter2: $2
echo '===========$#==============='
echo parameter numbers: $#
=================运行结果========================
script name: ./parameter.sh
parameter1: abc
parameter2: def
===========$#===============
parameter numbers: 2
```

## `$*` 和 `$`

输出所有参数

```bash
#!/bin/bash
echo ============$0===============
echo script name: $0
echo parameter1: $1
echo parameter2: $2
echo '===========$#==============='
echo parameter numbers: $#
echo '===========$#==============='
echo parameter numbers: $#
echo '===========$*==============='
echo $*
echo '===========$@==============='
echo $@
============运行结果============
============./parameter.sh===============
script name: ./parameter.sh
parameter1: abc
parameter2: def
===========$#===============
parameter numbers: 2
===========$#===============
parameter numbers: 2
===========$*===============
abc def
===========$@===============
abc def


```

# `$?`

最后一次执行命令的返回状态，如果这个变量的值为0，如果这个命令的值为0，证明上一个命令执行正确执行：如果这个变量的值非0(具体那个数，由命令自己来决定)，则证明上一个命令执行不正确了

