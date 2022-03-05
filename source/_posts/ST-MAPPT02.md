---
title: Markdown PPT | 如何自定义Marp主题
top: false
cover: false
toc: true
mathjax: true
summary: Markdown PPT | 如何自定义Marp主题
tags:
  - Markdown PPT
  - Markdown
categories: 软件
typora-root-url: ST-MAPPT02
abbrlink: 12936
date: 2022-03-02 19:54:02
password:
coverImg:
---

之前展示了自定义的果壳PPT的Marp主题，这次给大家介绍如何自定义Marp主题。



Marp主题的自定义有两种方式：

1. 如果你只想对当前主题进行微小改动，可以直接在md文件中添加命令修改；
2. 如果你想要大幅修改主题，需要编写CSS文件进行主题自定义。

## 1 md文件主题修改

### 1.1 全局命令和局部命令

Marp的全局命令是指写在首页，作用于全部Slide的命令，局部命令是指作用于本页的指令。虽然官网的介绍是两者命令不同，但在实际使用过程中，发现其实两者唯一的区别是 是否具有下划线，例如：

```
papaginate: true    //表示Slide标页码
_papaginate: false  //表示本页Slide不标页码
```

官网介绍的**全局命令和局部命令**

![img](v2-31be3538226e2e8f49ecbc5d15118240_720w.png)



编辑切换为居中

添加图片注释，不超过 140 字（可选）

![img](v2-a1ec245ea4a7d9c2d3b9f7bc0e68a507_720w.png)



编辑切换为居中

添加图片注释，不超过 140 字（可选）

**全局命令使用**

```
---
marp: true
theme: gaia
paginate: true
---
```

如上面展示的那样，全局命令可以直接将命令写到分割线内

**局部命令使用**

```
---
<!--
_backgroundImage: url("./images/bg1.jpg")
_paginate: false 
-->

---
```

如上面的展示的那样，局部命令的生效，需要在命令两端添加 <!-- -->。同样如果只想让命令在本页生效，需要在命令前添加下划线。

### 1.2 全局样式和局部样式

命令只能对Slide的小部分内容进行调整，如果想要对Slide的文字样式做出调整，那么就需要对全局样式和局部样式做出修改，支持CSS语法。

**全局样式修改**

```
---
marp: true
theme: gaia


style: |
  section {
    background-color: #ccc;
  }
  h1 {
    text-align:left;

  }
---
```

全局样式的修改是以 style 命令进行的，如上面展示的那样，我们可以在style命令中对样式进行相关修改。

**局部样式修改**

不过style命令并不支持下划线的局部命令，如果想要修改本页PPT的样式，需要以html的形式进行修改。

```
<style scoped>
    section {
  text-align: center;
    }
</style>
```

### 1.3 Markdown文件示例

根据上面所述，我们可以得到生成的markdown文件示例如下：

```
---

marp: true
theme: UCASSimple
paginate: true

---

<style scoped>
    section {
  text-align: center;
    }
</style>

<!--
_backgroundImage: url("./images/bg1.jpg")
_paginate: false
style:  
-->

![img w:400px h:80px](./images/logo.png)
#  h1样式
##  h2样式

**BeWater**
**2021-12-10**

---
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

![bg left:45%](./images/bg2.jpg)
# 目 录

###### 1 Slide 概述
###### 2 文字展示
###### 3 代码展示
 
---
```

## 2 CSS文件主题修改

如果你觉得上面的内容并不能满足你的需求，那你可能需要自定义CSS文件来改变Slide样式。

### 2.1 CSS文件配置

如果想要使用自己的CSS主题文件，你首先需要在当前md文件夹下新建.vscode 文件夹，在该文件夹下新建settings.json文件，添加如下内容。

```
{
    "markdown.marp.themes": [
      "https://example.com/foo/bar/custom-theme.css",
      "custom theme.css path",
    ]
  }
```

custom theme.css path  要添加自定义主题文件的路径，例如 ./themes/UCASSimple.css 

### 2.2 CSS文件内容

除去上面的文件，在CSS 文件头部需要添加 /* @theme <custom theme name>*/ 来声明是这是一个Marp主题，这样在编写.md 文件时就可以借助 theme: <custom theme name> 使用自定义的主题了。

 随后CSS文件中需要利用@import  导入已有的主题文件，目前Marp官方有default gaia uncover 三款主题。

接着就可以编写CSS文件自定义主题了。

### 2.3 CSS文件示例

```
/* @theme UCASSce */

@charset "UTF-8";
@import 'uncover';

section {
   font-size: 25px;
   padding: 50px;
   text-align: left;
   font-family:Arial, Helvetica, sans-serif;
   background:whitesmoke;
  }
 
  h1 {
   text-align:left;
   color: rgb(60, 112, 198);
   margin-top: 150px;
   margin-bottom: 0px;
   font-size:72px;
  }

  header {
    left: 50px;
    right: 50px;
    top: 10px;
    height: 50px;
    background-image: url("./images/logo.png"); 
    background-position: right top;
    background-repeat: no-repeat;
    background-size: 200px;
    text-align:left;
    color: rgb(60, 112, 198);
    font-weight: bold;
    font-size:36px;
  }
```

## 参考& 更多阅读

[Marp 官网教程](https://marpit.marp.app/)

[CAI Marp中文教程](https://caizhiyuan.gitee.io/categories/skills/20200730-marp.html)
