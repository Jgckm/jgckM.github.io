---
title: 使用部署Valine-Admin失败
abbrlink: d7556a16
date: 2022-08-14 20:07:26
categories:
- [博客]
- [JavaScript]
tags:
  - JavaScript
  - nodejs
  - 博客 
cover: https://s1.ax1x.com/2022/08/15/vaNgAO.jpg
keywords: butterfly 评论系统搭建，Valine，Valine-Admin
description: Valine-Admin部署报错
---

# 前言

> 最近在对接博客评论系统中，遇到了一个小问题，上网搜索没有相关的教程。于是就想着自己记录一下，防止哪天自己又忘记了

博客使用的是 [Valine](https://www.leancloud.cn/) 评论系统，优点事省事、简洁、免费。

# 🙃遇到问题

在**部署**的时候出现出错误

![报错信息](https://s1.ax1x.com/2022/08/15/vaYbsP.png)



部署用的是[Valine-Admin](https://github.com/zhaojun1998/Valine-Admin)仓库，后来在 **issues** 找到了，出现问题的原因

是因为 Valine-Admin 不再支持 nodejs 11.x 版本的，直接 使用 nodejs 12.x 就可以。这里附上地址[解决方案地址](https://github.com/zhaojun1998/Valine-Admin/pull/3)

# 🎉解决方案

1. fork 仓库

2. 修改 **package.json** 这个文件 将 node 从 **11.x** 改为 **12.x** 

   ```json
     "engines": {
       "node": "12.x"
     }
   ```

   

   附上地址 [package](https://github.com/jgckM/Valine-Admin/blob/master/package.json) 

3. 提价更改

4. 在部署的时候直接使用 自己fork 的仓库仓库地址

   ![成功重新部署](https://s1.ax1x.com/2022/08/15/vatJFe.png)

5. 此时已经成功部署，问题解决

# 🎨博客评论介绍

直接在 **昵称** 填写 QQ 可以自动获取 QQ昵称 和 QQ邮箱 省去很多时间来填写

## 为啥要填写邮箱

填写邮箱后方便通知你，比如别人回复了你的评论，评论系统会发送邮件提醒你。

# 🧵写在最后

如果你也遇到次中情况，可以直接 frok 我的仓库[**Valine-Admin**](https://github.com/jgckM/Valine-Admin) 😜
