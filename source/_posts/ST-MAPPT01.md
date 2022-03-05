---
title: 用Markdown写PPT ，Marp的果壳主题
top: false
cover: false
toc: true
mathjax: true
summary: 用Markdown写PPT ，Marp的果壳主题
tags:
  - Markdown
  - Markdown PPT
categories: 软件
typora-root-url: ST-MAPPT01
abbrlink: 41224
date: 2022-03-02 19:53:53
password:
coverImg:
---



前段时间，一直有小果壳er们寻找Latex或者Markdown的PPT模板，小冰近期终于抽出时间赶出了一套基于Markdown的PPT模板。

**上图**

简约学术蓝风格

![img](v2-e2db49b72ea7f77b965cae3516d9ed6f_720w.jpg)



编辑切换为居中

添加图片注释，不超过 140 字（可选）

![img](v2-df2970557ead1ad2d6df2639b57aecb5_720w.jpg)



编辑切换为居中

添加图片注释，不超过 140 字（可选）

![img](v2-5c69b40f41bd80f7b5a4e6ba3797178e_720w.jpg)



编辑切换为居中

添加图片注释，不超过 140 字（可选）

![img](v2-6048140d93314418d1958d6e9ea25ef7_720w.jpg)



编辑切换为居中

添加图片注释，不超过 140 字（可选）

![img](v2-5e1468af9442679bc0949171d302abbe_720w.jpg)



编辑切换为居中

添加图片注释，不超过 140 字（可选）

![img](v2-d6fad12f8bd25606f9e780ea6699bbc7_720w.jpg)



编辑切换为居中

添加图片注释，不超过 140 字（可选）

![img](v2-bc5d65927bdec29528e644863710f10e_720w.jpg)



编辑切换为居中

添加图片注释，不超过 140 字（可选）

![img](v2-e139d8cf65be410bfe14c883a978c90f_720w.jpg)



编辑切换为居中

添加图片注释，不超过 140 字（可选）

风景风格

![img](v2-41ee627e7bc0e477996f28e8586d92bc_720w.jpg)



编辑切换为居中

添加图片注释，不超过 140 字（可选）

![img](v2-22952ae75e62ea0a33c0f846935fcce1_720w.jpg)



编辑切换为居中

添加图片注释，不超过 140 字（可选）

![img](v2-c6b2783575e1a1e79b8d487e154ea05e_720w.jpg)



编辑切换为居中

添加图片注释，不超过 140 字（可选）

![img](v2-eee9ddf19e9e596e6000dd101c6839f2_720w.jpg)



编辑切换为居中

添加图片注释，不超过 140 字（可选）

上面两套PPT均基于**VSCode插件Marp** 编辑而成，能够满足日常汇报PPT需求，**同时公式、代码编辑比Office排版美观**。

## **Marp介绍**

Marp官网：

Marp: Markdown Presentation Ecosystemmarp.app![图标](v2-0eabba0d7ed4c14d58f78f56f5e5e31d_180x120.jpg)

Marp是一款基于markdown开发的PPT软件，让我们专注于PPT的内容，而不再花费过多的时间排版，当然，其并不能像Office那样高自由度的排版，但满足日常汇报足够。

目前Marp已有单独的软件和VsCode插件，小冰使用的是VScode插件。

## **Marp安装与使用**

打开VsCode 的扩展主题 搜索 Marp即可进行安装。

Marp使用也非常简单，其利用markdown的分隔符对PPT进行分页。

举个栗子

```
---
marp: true
theme: gaia
paginate: true

---

# 汇报题目 h1样式
## 副标题 h2样式

**BeWater**
**2021-12-10**
---
```

上面代码生成的PPT如下

![img](v2-ea454b30012d831aecd2f357ce866dde_720w.png)



编辑切换为居中

添加图片注释，不超过 140 字（可选）

相关语法可以参考CAI的博客 

marp Markdown演示编写器 | CAIcaizhiyuan.gitee.io![图标](v2-88b8598c2de8ad4d9d5205dc847a2f29_ipico.jpg)

如果需要导出PDF、PPT等格式文件，只需要点击左上角的按钮，选择Export即可，但导出的PPT是图片，并不能进行编辑。

![img](v2-537fcfa5f937e00cdbcaf6ce4af95b52_720w.png)



编辑

添加图片注释，不超过 140 字（可选）

## **UCAS主题**

Marp官方只提供了default gaia uncover 三款主题，并不能完全满足我们的日常使用。

我们可以通过css文件自定义主题进行使用，开头展示的PPT就是小冰自定义的主题。如果你觉得这两个主题完全够用，你可以直接安装这两个主题进行使用，logo可以进行替换。

github链接：

https://github.com/BeWaterMyFriend7/Marp-Theme-UCASgithub.com

如果访问github不方便，可以后台回复 **Marp** 获取压缩包。

下载之后,在Vscode成功安装了Marp的基础上，你可以利用Vscode打开该文件夹，直接修改.md文件生成自己的PPT文件即可。

在使用主题之前，建议**先看一下生成的PDF文件暨主题介绍文件**。

## **主题介绍**

小冰自定义了两款Marp主题 UCASSimple 简约蓝色块和 UCASSce 果壳风景主题，其实两款主题基本一样，只是首尾页和目录页进行了微小改动。两款主题对应的md文件分别是SimpleBlue.md，Scenery.md，对应的pdf文件是./doc/SimpleBlue.pdf，./doc/Scenery.pdf

文件结构如下：

```
Marp
  |__ .vscode
  |     |__settings.json   //主题配置文件
  |__ doc
  |     |__Scenery        //Scenery.md 生成的PPT图片
  |     |__SimpleBlue     //SimpleBLue.md 生成的PPT图片
  |     |__Scenery.pdf    //Scenery.md 导出的Pdf
  |     |__SimpleBlue.pdf //SimpleBlue.md 导出的Pdf
  |__ images              //文稿和主题所用到的图片文件 可对背景和logo进行替换
  |__ themes
  |     |__UCASSce.css    //UCASSce主题文件
  |     |__UCASSimple.css //UCASSimple主题文件
  |__Scenery.md           //UCASSce主题对应的md文件
  |__SimpleBlue.md        //UCASSimple主题对应的md文件
```

## **md文件介绍**

以下简单介绍以下Scenery.md文件，方便果壳er使用。

首先是Marp主题的选择和部分全局命令。

```
---
marp: true
theme: UCASSce
paginate: true
---
```

接下来是**首页内容** <!-- _paginate:false -->表示本页PPT不标页码，是局部命令。 为了调整文字和背景图片，小冰在正式文字前加了很多空行。

如你所见，首尾页图片背景是直接使用PPT绘制了一整张图片作为背景进行实现的，UCASSimple主题也是这样实现的，并不是插入图片调整图片位置和大小实现的，因此如果你想要更换背景，需要利用PPT做一张16:9的背景图片进行替换。

```
<!--
_paginate: false
-->
![bg vertical w:1300px](images/bg3.jpg)
<br/>
<br/>
<br/>
<br/>
# 汇报题目 h1样式
## 副标题 h2样式
**BeWater  2021-12-10**
---
```

**目录页**：<style scoped>...</style> 是局部样式调整，目录的各个小标题采用h6样式，全套PPT仅有目录页使用了h6样式。

```
<style scoped>
    section {
  text-align: center;
    }
    h1 {
        color: rgb(60, 112, 198);
        margin-bottom: 30px;
    }
    h6 {
        text-align: center;
    }

</style>
<!--
_paginate: false 
-->

![bg left:55% ](./images/bg5.jpg)
# 目 录

###### 1 Slide 概述
###### 2 文字展示
###### 3 代码展示
###### 4 公式展示
###### 5 表格展示
###### 6 图片展示
###### 7 其它展示
###### 8 参考文献&引用展示
```

**正式内容页**:<!-- _header: 1 Slide概述 --> 是PPT的最上方标题栏的实现，文字内容需要根据实际情况进行调整。

```
<!-- _header: 1 Slide概述 -->

本PPT借助插件Vscode插件Marp书写而成，由markdown文档编辑，方便公式和代码的展示与排版。

**环境：**
- 系统：Win10
- 软件：VsCode 插件：Marp
- theme：自定义主题 UCASSce ，基于官方uncover主题修改
  
**特征：**
- 背景选用果壳风景，每页上方标题栏基于Marp header格式进行修改而成。
- 首尾页和目录页图片基于背景得到，首尾页可根据文字内容在本页修改标题样式，目录页可根据文字内容对图片进行大小位置调整
```

**小冰对CSS和一些前端知识并不是很熟悉，只是现学现用，编码难免有所不妥，还望见谅~同时欢迎熟悉前端的大佬对主题提出修改意见**
