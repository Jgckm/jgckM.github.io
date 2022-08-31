---
title: centos7安装
tags:
  - Linux
  - CentOS
categories:
  - Linux
abbrlink: 9bbb7be6
date: 2022-08-15 08:29:12
cover: https://cdn.jsdelivr.net/gh/jgckM/image@main/cover/202208180938073.jpg
---
# ✨CentOS 7 安装

> 安装 centos7 为学习 Linux 系统 打下基础

## ⚙下载 地址 [CentOs7](https://www.centos.org/download/)

## 🎨安装

配置好虚拟机之后就可以启动虚拟机进行安装了

启动后会有引导界面直接选择第一个 `Install CentOs 7` 进行安装![install centos7](https://cdn.jsdelivr.net/gh/jgckM/image@main/image/202208152022741.png)

等待进入欢迎界面 选择对应的语言 后点击**继续**![选择语言](https://cdn.jsdelivr.net/gh/jgckM/image@main/image/202208152027367.png)

找到 **最小环境** 点击进入 找到 **GNOME 桌面**点击**完成**

![选择GNOME桌面](https://cdn.jsdelivr.net/gh/jgckM/image@main/image/202208152040773.png)

点击 **安装位置** 进行磁盘分区  点击**我要分区**![点击我要分区](https://cdn.jsdelivr.net/gh/jgckM/image@main/image/202208152055794.png)

手动分区 => 挂载方案选择 **标准分区**

![点击 +](https://cdn.jsdelivr.net/gh/jgckM/image@main/image/202208152059329.png)

手动分区

| 挂载点 |          设定容量           |          |  文件类型  |
| :----: | :-------------------------: | :------: | :--------: |
| /boot  |             1G              | 引导分区 |    xfs     |
|  swap  | 2G (实际内存的1被或2被之间) |  交换区  | 必须是swap |
|   /    |             37G             |  根分区  |    xfs     |

- `xfs`是新型的默认即可

![image-20220815212113681](https://cdn.jsdelivr.net/gh/jgckM/image@main/image/202208152121815.png)

点击 **完成** => **接收更改** 

找到`KDUMP` 关闭 （实际开发需要开启，这是当内核崩溃是捕获错误的）

配置 网络和主机名
1. 主机名：hadoop10 还要点击 **应用**![image-20220815213001578](https://cdn.jsdelivr.net/gh/jgckM/image@main/image/202208152130709.png)

点击 **开始安装**

设置 root 密码

创建普通用户
1. 设置用户名
2. 设置密码

等待安装完成 重启即可

重启后要接收许可证 然后 完成配置

点击 未列出 即可登录 root 用户

进入欢迎界面 选择好**语言**![选择语言](https://cdn.jsdelivr.net/gh/jgckM/image@main/image/202208160840424.png)

输入法也选择 汉语

位置服务要关闭

在线账号 跳过即可 

直接点击开始使用

到这一步安装完成了

# 🧵后记

下载centos7是可以选择国内的镜像，比如阿里，163的、南京大学的等这些在国内的镜像速度都是挺快的