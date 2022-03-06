---
title: Hexo主题更换和优化
top: false
cover: false
toc: true
mathjax: false
tags:
  - hexo
  - Blog
  - Github
  - matery
categories: 编程技术
author: BeWater
summary: Hexo主题更换和优化
typora-root-url: TH-Blog-003
abbrlink: 57447
date: 2022-03-06 14:52:15
img:
password:
---

搭建完blog ，接下来就是更换一个漂亮的主题了。

由于下面的操作配置可能会出现失误，因此建议配置完一部分，就在本地测试一下，看看效果，以免出现错误难以定位，还得从头再来。

## 主题更换

### 主题推荐

https://hexo.io/themes/  

https://siricee.github.io/hexo-theme-Chic/ 

https://dewjohn.github.io/   

https://blinkfox.github.io/  

### 主题下载更换

本部分主要以**matery**主题为例进行测试说明

[hexo-theme-matery 主题文档](https://github.com/blinkfox/hexo-theme-matery/blob/develop/README_CN.md)

本地 `blog/themes` 目录下 clone 主题文件，或者在GitHub页面下载，然后将解压缩的文件夹直接放到themes 目录下，注意**修改名字为hexo-theme-matery**

```bash
git clone https://github.com/blinkfox/hexo-theme-matery.git
```

blog目录下的 `_config.yml`修改如下内容

```bash
theme : hexo-theme-matery
per_page : 12/18(两处)

# 修改title author等信息
url : <url 你的blog地址>
```

### 基础配置

随后按照主题[说明文件](https://github.com/blinkfox/hexo-theme-matery/blob/develop/README_CN.md)新建一系列右上角跳转页面和一些扩展功能

在该主题文件下的配置文件`_config.yml`进行属性修改

```html
blog/themes/hexo-theme-matery/_config.yml

menu部分：
	#见不需要未新建跳转页面的直接注释
 dream 如果不需要直接false
 indexbtn 修改为自己的github地址
 sociallink 修改为自己的社交账号信息
 reward 直接修改为false
 
 profile:修改关于界面信息
 #其它关于信息直接修改为false
 
 githublink 修改为自己的github
 
 subtitle 修改信息
 
```

主题文件中需要更改的图片

```bash
# 配置网站favicon和网站LOGO
favicon: /favicon.png
logo: /medias/logo.png

# 修改背景
medias/cover.jpg
medias/banner/ 下的图片 
medias/featureimages 下的图片

#关于界面个人头像
/medias/avatar.jpg

# 总之 medias的图片全部更改为自己喜欢的即可
# 需要注意的是，一些文件夹下的图片数量如果更改，主题配置文件也需要修改，以下详细介绍
```

## 主题优化

### 文章头设置

```bash
#为了新建文章方便，将/scaffolds/post.md修改为如下代码：相关属性可以看主题说明文档 

---
title: {{ title }}
date: {{ date }}
author: 
img: /source/images/xxx.jpg
top: false
cover: false 
password:
toc: true
mathjax: false
summary:
tags: 
- hexo
categories: blog
---
```

### 文章首图设置



img 表示文章的首图，默认不特殊标注

此时会从主题文件下的 `source\media\featureimages`文件夹下，此文件夹下有0-23 一共24张图片，我们可以更换为我们自己喜欢的图片，如果你要更改其图片数量，需要在主题文件的 `_config.yml`文件下进行更改：

```html
featureImages:
# 在下面进行更改文件名称
- /medias/featureimages/0.jpg
```

如果img特殊标注，那么就会按照指定路径展示文章首图

### 增加社交账号信息

原主题的社交账号很多不需要可以直接注释，如果想要添加主题配置文件`_config.yml`中不存在的社交账号，需要进行如下操作：

主题文件夹下 /layout/_partial/social-link.ejs 增加社交账号信息 

图标可以在 [Fontawesome](https://fontawesome.com/icons) 中找到相关代码

```bash
<% if (theme.socialLink.daohang) { %>
    <a href="<%= theme.socialLink.daohang %>" class="tooltipped" target="_blank" data-tooltip="进入果壳er导航页: <%= theme.socialLink.daohang %>" data-position="top" data-delay="50">
        <i class="fas fa-compass"></i>
    </a>
<% } %>
```

主题文件夹的配置文件`_config.yml`中

```html
sociallink部分增加
daohang： https://xydh.fun/ucas
```

### 重新配色

原来主题使用了大量的绿色，我们可以替换为自己喜欢的颜色，如果不知道渐变色如何调，可以参考 [webgradients ](https://webgradients.com/)。

主题文件夹 `\source\css\matery.css` 文件中

将 `#4cbf30`  `#0f9d58 `修改为自己喜欢的颜色代码。

### 首页背景轮播逻辑



主题原本的首图背景切换逻辑是一周一张图片，这里我更改为了刷新一次就更换背景图片

在 `主题文件夹\layout\_partial\post-detail-toc.ejs` 文件中

```javascript
// 原始文件内容
<script>
    // 每天切换 banner 图.  Switch banner image every day. 这两行需要更改
    var bannerUrl = "<%- theme.jsDelivr.url %><%- url_for('/medias/banner/') %>" + new Date().getDay() + '.jpg';
    $('.bg-cover').css('background-image', 'url(' + bannerUrl + ')');


</script>
<% } else { %>
<script>
    $('.bg-cover').css('background-image', 'url(<%- theme.jsDelivr.url %><%- url_for('/medias/banner/0.jpg') %>)');
</script>
<% } %>
  
// 将4-5行替换为如下内容   8 表示主题文件\source\medias\banner 下的图片数量
var x = Math.floor(Math.random() * 8);
var bannerUrl = "<%- theme.jsDelivr.url %><%- url_for('/medias/banner/') %>" + x + '.jpg';
$('.bg-cover').css('background-image', 'url(' + bannerUrl + ')');
```

### 文章评论



Matery主题默认关闭了文章评论功能，如果我们想要打开文章评论，我们需要对配置文件修改

#### 注册LeanCloud

注册一个 [LeanCloud账号](https://console.leancloud.cn/apps) ，实名验证后，在控制台后 **创建应用**

应用创建完成后在 **设置>应用凭证** 中 获取 `App ID` 和 `AppKey`

#### 主题config 文件配置

`_config.yml` 中修改如下内容

```html
valine:
  enable: true
  appId: <刚才获取的APPID>
  appKey: <刚才获取的APPKey>
  notify: false
  verify: true
  visitor: true
  avatar: monsterid
  guest_info: nick,mail,link
  pageSize: 10
  placeholder: 'just go go' 
  language: zh-cn
  comment_count: true 
```



## Reference & More Reading

[hexo-theme-matery 主题文档](https://github.com/blinkfox/hexo-theme-matery/blob/develop/README_CN.md)

[知乎 godweiyang hexo+Github 博客搭建小白教程](https://zhuanlan.zhihu.com/p/35668237)

[Nicethemes 主题个性化配置](http://nicethemes.cn/news/txtlist_i35928v.html)

 [md文件示例](https://www.cnblogs.com/anthony-wang0228/articles/11461321.html)

[CSDN cungudafa matery主题 颜色 背景 滚动条优化 增加点击评论](https://blog.csdn.net/cungudafa/article/details/106278206)

[Valine 文档](https://valine.js.org/quickstart.html)  

[评论添加教程 by  luckyzmj](http://luckyzmj.cn/posts/1d6f1579.html)

[过客～励む blog 主题个性化修改1](https://yafine-blog.cn/posts/8c84.html)

[过客～励む matery主题个性化修改2](https://yafine-blog.cn/posts/12b4.html)

[江南骚年 blog matery 主题美化](https://www.cnblogs.com/coderma/p/13527261.html)
