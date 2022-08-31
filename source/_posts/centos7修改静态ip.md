---
title: centos7修改静态ip
abbrlink: f6ab952a
date: 2022-08-16 18:34:56
tags:
  - Linux
  - CentOS
cover: https://cdn.jsdelivr.net/gh/jgckM/image@main/cover/202208170851827.png
categories:
  - Linux
---

> - 来一发linux 修改静态ip的记录
> - 要配置和电脑主机在同一ip网段下方便链接

# ⚙打开终端

`vim /etc/sysconfig/network-scripts/ifcfg-ens33`进入编辑页面

```
TYPE="Ethernet"
PROXY_METHOD="none"
BROWSER_ONLY="no"
BOOTPROTO="dhcp"
DEFROUTE="yes"
IPV4_FAILURE_FATAL="no"
IPV6INIT="yes"
IPV6_AUTOCONF="yes"
IPV6_DEFROUTE="yes"
IPV6_FAILURE_FATAL="no"
IPV6_ADDR_GEN_MODE="stable-privacy"
NAME="ens33"
UUID="03da8ded-3662-437c-97c8-f0194fbc8a9d"
DEVICE="ens33"
ONBOOT="yes"
```

# 🛠修改第4行的配置

- ##  修改`BOOTPROTO="dhcp"`

1. 按键盘的 `4gg` 跳到第四行 `ww`跳到 dhcp 在按 `dw`删除 dhcp
1. 按`i`进入编辑模式填写 static
1. 按 `Esc`退出编辑模式

```
BOOTPROTO="static"
```

# 🥽 添加IP配置

1. 复制下面代码
2. `Shift`+`g`快速跳到最后一行
3. 按`o`进入编辑模式
4. `Ctrl`+`Shift`+`v`粘贴代码
5. 如果要是不同ip可以使用左右可控制键来进行修改
6. `:wq`保存并退出


```
# IP地址
IPADDR=192.168.131.100
# 网关
GATEWAY=192.168.131.2
# 域名解析器
DNS1=192.168.131.2
```

- ## 🧨配置的网段前面要相同

- IPADDR 后面的可以最后一个随便写  `192.168.131.xxx`

![image-20220816190933516](https://cdn.jsdelivr.net/gh/jgckM/image@main/image/202208161909705.png)

# 🎉重启服务

在终端输入 

```
service network restart 
```

# 问题总结

1. 物理机能 ping 通虚拟机，但是虚拟机ping不通物理机，一般都是物理机的防火墙问题，把防火墙关闭就行
2. 虚拟机能 ping 物理机，但是虚拟机 ping 不通外网，一般都是DNS设置有问题
3. 虚拟机 ping www.baidu.com 显示域名未知等信息，一般查看 GATEWAY 和 DNS 设置是否正确(踩坑2小时)
4. 如果以上全部设置还是不行，需要关闭 NetworkManager 服务

   - systemctl stop NetworkManager  关闭

   - systemctl disable NetworkManager  禁用


5. 如果检查发现 systemctl status network  有问题  需要检查  ifconfig-ens33
