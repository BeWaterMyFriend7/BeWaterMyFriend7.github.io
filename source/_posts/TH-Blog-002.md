---
title: Hexo + Github 个人博客搭建过程
top: false
cover: false
toc: true
mathjax: false
tags:
  - hexo
  - Blog
  - Github
categories: 编程技术
author: BeWater
summary: Hexo + Github 个人博客搭建过程
typora-root-url: TH-Blog-002
abbrlink: 26764
date: 2022-03-06 14:52:10
img:
password:
---

本部分搭建过程主要参考 [知乎 godweiyang 的教程](https://zhuanlan.zhihu.com/p/35668237)

## 前期准备

### 安装Node.js

https://nodejs.org/en/

下载之后一路next ，一些tools可以不用选择安装

**安装测试**

安装后输入命令 `node -v`  `npm -v` 如果出现版本号，那么安装成功

安装过程中可能需要翻墙

或者添加国内源进行加速

```bash
npm config set registry https://registry.npm.taobao.org
```

### Git 和 GIthub 配置

安装Git 同时注册GIthub账号 同时将GIthub与本地进行配置连接

```bash
# 右键打开bash 终端 进行配置  
git config --global user.name ""
git config --global user.email ""

#生成密钥
ssh-keygen -t rsa -C "email.address"

#github web settings>SSH and GPG keys 新建一个SSH 

cat ~/.ssh/id_ras.pub

#输出内容复制到GitHub web 中的框中，点击保存 

#bash 中输入
ssh -T git@github.com 

#如果出现你的GitHub信息表示成功了
```

## 创建Blog 目录

### GIthub新建blog仓库

仓库名称 `Github账号.github.io` 同时勾选初始化 `Readme`

仓库`Settings`界面找到 `Github Pages` 点击 `Choose a theme`选择主题，稍等一会儿。

![img](1646463964999-b56f12b2-89d7-4a4d-9750-a661b5785bfc.png)



点击blog链接，此时应该有一个网页出现了，这就是你的blog



![img](1646463995044-4aab6ded-1a68-42c4-99ef-57c015b65d9a.png)



### 安装Hexo

#### 初始化本地blog文件夹

**本地新建一个blog存放目录**

打开git 命令行定位到该目录下 

```bash
npm i hexo-cli -g 				#安装hexo
hexo -v 									#验证hexo是否安装成功
hexo init 								#初始化文件夹
npm install 							#安装必备组件
npm i hexo-deployer-git   #安装部署工具
```

#### 本地blog文件夹与Github建立连接

本地博客文件夹根目录下 `_config.yml`  修改如下内容

```bash
deploy:
  type: git
  repository: https://github.com/github 账号/ .github.io
  branch: master
  
url : <url 你的blog地址>
```

之前github新建一个仓库会默认新建分支 `master`但现在默认分支名称为 `main`,因此你可以在上述 `branch`中修改为 `main` 或者更改github仓库名称。

### 文章测试

```bash
#新建一篇文章 ，此时source\_posts 目录下就多了一个md文件

hexo new post article title		

# 修改文章内容，运行如下命令就可以看到自己的blog了。

########  test   ##########
hexo g								#生成静态网站
hexo s								#打开本地服务器，对网站进行预览
hexo d 								#上传github
```

## Reference & More Reading

[知乎 godweiyang hexo+Github 博客搭建小白教程](https://zhuanlan.zhihu.com/p/35668237)

[知乎 直上云霄 如何搭建个人独立博客回答](https://www.zhihu.com/question/20463581/answer/489125915)

[知乎 果果小师弟 GIthub+Hexo +matery 博客搭建小白教程](https://zhuanlan.zhihu.com/p/123286944)

 [百度推送](https://blog.csdn.net/tianjuewudi/article/details/112504019)

 [AnthonyWang hexo 发布文章](https://www.cnblogs.com/anthony-wang0228/articles/11461321.html)

