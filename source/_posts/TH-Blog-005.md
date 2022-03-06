---
title: Hexo 博客多终端同步问题
top: false
cover: false
toc: true
mathjax: false
tags:
  - hexo
  - Blog
categories: 编程技术
author: BeWater
summary: Hexo 博客多终端同步
typora-root-url: TH-Blog-005
abbrlink: 18527
date: 2022-03-06 14:52:31
img:
password:
---

如果你已经在一台电脑上完成了博客的搭建，那么你是否想过如何在其它电脑上同步博客呢~

其实原理很简单，`hexo g`将我们的源文件部署， `hexo d`上传的只是网页部署文件，这些文件上传到了 github的 `master`分支，我们在另一台电脑上如果能够拥有源文件的话，同样将这些部署文件上传到 github 的 `master`分支即可，那么其实我们要做的就是备份源文件。

那么我们可以在github的blog仓库新建一个分支，存储源文件，亦或者新建一个仓库，存储源文件即可，这样我们就可以在多个终端间同步源文件，而后就可以进行博客文件的终端同步了。

## 多终端同步配置

### Github 操作

github Blog仓库中**新建一个分支 hexo**

![img](1646448217689-e5a1805e-0b19-4aa3-bd8c-45cdf5d1b9da.png)

settings 选择**默认分支 hexo**

![img](1646448393409-c5f39d47-2b08-4f5f-a5a4-782071492125.png)



### 初始电脑本地操作

本地任意一空白目录下 git clone 之前的代码

```bash
git clone git@github.com:<your rep url ,eg :name.github.io.git>
```

clone成功后，删除掉除去`.git`之外的所有文件夹

把之前的博客源文件复制过来，除去 `.deploy_git`

新建or修改 `.gitignore`文件 

```bash
.DS_Store
Thumbs.db
db.json
*.log
node_modules/
public/
.deploy*/
```

如果你在`themes`文件夹下 clone 过其它主题文件，把其中的 `.git`文件夹删除掉

上传文件到hexo分支

```bash
git add .
git commit -m "backup blog source file0305"
git push 
```

如果没有报错，此时github端应该就可以看到备份的源文件了。

### 另一台终端操作

进行一些基础配置，安装git nodejs 配置git连接Github

```bash
npm install hexo-cli -g			# intall hexo

# 在该电脑的本地文件夹下clone Blog源文件
git clone <url>
```

![img](1646456436371-e368eb6e-a5c4-4ea5-8302-d765b0744d7c.png)



clone 成功后，进入blog文件夹下，安装之前安装的插件

```bash
npm install
npm install hexo-deployer-git --save
npm install hexo-hexo-renderer-marked #图片
```

然后就可以在新电脑上写博客了，将博客部署到网站后，记得备份源文件

```bash
git add .
git commit -m ""
git push 

## github端 同步到 本地 ##
git pull
```

## Reference

[知乎 直上云霄 【使用hexo，如果换了电脑怎么更新博客？】问题回答](https://www.zhihu.com/question/21193762/answer/489124966)  

[知乎 godweiyang 超详细 Hexo+Github 博客搭建小白教程](https://zhuanlan.zhihu.com/p/35668237)
