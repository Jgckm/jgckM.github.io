---
title: vue打包后引入js和css用相对路径引入
tags:
  - vue
  - Github
cover: 'https://cdn.jsdelivr.net/gh/jgckM/image@main/cover/202208301502698.jpg'
categories:
  - Vue
abbrlink: 23840d68
date: 2022-08-30 15:00:05
---

# ✨前言

今天使用Vue打包后上传至Github Pages 静态托管，一打开白屏啥都没有

![image-20220830150852279](https://cdn.jsdelivr.net/gh/jgckM/image@main/image/202208301508438.png)

白茫茫一片啥都没有。（哎，这啥情况😑）

# 🔎寻找问题

接着 `F12`看来一下

![image-20220830151019323](https://cdn.jsdelivr.net/gh/jgckM/image@main/image/202208301510394.png)

红了一大片，显示资源没找到？我接着又回去找源文件看了才发现问题，特此记录

![image-20220830151224995](https://cdn.jsdelivr.net/gh/jgckM/image@main/image/202208301512056.png)

在打包生成的文件 `index.html`找到问题所在

![image-20220830151418978](https://cdn.jsdelivr.net/gh/jgckM/image@main/image/202208301514037.png)

所有静态资源都用的是`绝对路径`使用绝对路径直接导致资源无法找到

![image-20220830151610205](https://cdn.jsdelivr.net/gh/jgckM/image@main/image/202208301516290.png)

这样资源肯定是找不到的，所以得用`相对路径`

# ⚙解决问题

`绝对路径`行不通那就`相对路径`

在项目中找到 `vue.config.js`文件配置

![image-20220830152131192](https://cdn.jsdelivr.net/gh/jgckM/image@main/image/202208301521258.png)

添加如下代码：(这里有坑往下看)

```js
module.exports = {
  publicPath: "././",
  outputDir: "dist",
};
```

最后重新打包即可看到页面内容了

```
npm run build
```

# 🛹踩坑

这之后，我又开始在本地环境跑，Github Pages 上面跑的好好的，但是在本地环境运行不了呢

前前后后整了2个多小时，才找到答案

```js
module.exports = {
  publicPath: process.env.NODE_ENV === "development" ? "./" : "././",
  outputDir: "dist",
};
```

改成这个样子才可以
