---
title: Typora配置图片自动上传到图床
abbrlink: 5e37b811
date: 2022-08-15 11:13:54
tags:
    - 博客
    - 图床
cover: https://cdn.jsdelivr.net/gh/jgckM/image@main/cover/202208151720690.png
categories: 博客 
keywords: github搭建图床+jsdelivr CDN加速
description: 写博客必备的图床，自己手动搭建一个github+jsdelivr
---

# ✨前言

> 因为写博客的时候图片需要手动的插入，实在是麻烦，这种繁琐重复的事，很是让人烦。所以就打算作个图床，一开始用`gitee`对国内友好点，可是他好像不是为人民服务的那种，各种的反链，恶心。最终选择用github+jsdelivr 搭建

# 🥟使用的工具

- [**PicGo**](https://github.com/Molunerfinn/PicGo) 是一款优秀的图床上传工具 可以快速上传图片到图床的工具
- [**Typora**](https://typoraio.cn/) markdown编辑器

- github 用于存储图片

- github-plus PicGo 里面的插件 可以删除图片和同步仓库，而自带的版本不能删除

> 这边使用`PicGo+github`来实现markdown图床

# 🍭下载

进入`PicGo` 的github[下载页面](https://github.com/Molunerfinn/PicGo/releases)

![下载 PicGO](https://s1.ax1x.com/2022/08/15/va5fj1.png)

这里根据自己系统选择，我是win版。下载后无脑安装

成功安装界面

![界面](https://s1.ax1x.com/2022/08/15/vaIfPg.png)

# 🍿创建github仓库

然后初始化仓库（省略）

# 🌭配置PicGo

在**PicGo**找到 **图床设置** 找到 github图床

## token创建

1. 点击`setting`![setting](https://cdn.jsdelivr.net/gh/jgckM/image@main/image/202208151605800.png)
2. 进入设置界面看做下脚![](https://cdn.jsdelivr.net/gh/jgckM/image@main/image/202208151607476.png)
3. 下面就是点击`Personal access tokens` => `Generate new token` 生成`token`并且复制

4. 基本配置如下![image-20220815161331183](https://cdn.jsdelivr.net/gh/jgckM/image@main/image/202208151613288.png)

   ## 重点说一下

   推荐：使用**github-plus**

   ![github-plus](https://cdn.jsdelivr.net/gh/jgckM/image@main/image/202208160813762.png)
   
   配置基本一样![github-plus配置](https://cdn.jsdelivr.net/gh/jgckM/image@main/image/202208160815270.png)
   
   > 设定仓库名：要设置你自己的仓库   格式： 用户名/仓库名
   
   用 `jsdelivr` CDN加速 速度不用说了
   
   ```
   https://cdn.jsdelivr.net/gh/jgckM/image@main
   
   https://cdn.jsdelivr.net/gh/用户名/仓库名@分支名/仓库文件路径
   ```

设置完了点击 **确定**  和 **设为默认图床**

配置重命名(防止图片重名)![设置重命名图片](https://cdn.jsdelivr.net/gh/jgckM/image@main/image/202208151638323.png)

#  🍔Typora 配置

![配置Tyora上传](https://cdn.jsdelivr.net/gh/jgckM/image@main/image/202208151639825.png)

### ✅好了这样就大功告成了，以后图片粘贴进 Typora 就会自动上传，不需要在手动上传了，速度还是不错的
