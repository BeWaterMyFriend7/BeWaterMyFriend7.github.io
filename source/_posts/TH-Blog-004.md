---
title: Hexo博客图片和公式问题
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
summary: Hexo博客图片和公式问题
typora-root-url: TH-Blog-004
abbrlink: 23710
date: 2022-03-06 14:52:20
img:
password:
---

我构建blog过程中最大的问题可能就是 图片和公式的问题，图片网页端无法加载，公式网页端无法渲染等问题，困扰了我好久。

# 图片加载不出来的问题

网上很多关于 `hexo-asset-image 、img 、for hexo5` 等系列插件，我测试后发现并不起作用。  

## Hexo部分

最后是安装 `hexo-renderer-marked`插件，实验成功  

blog 目录下 `git bash here` 

```bash
npm install hexo-renderer-marked  #安装包
```

在blog目录`_config.yml`添加/修改如下内容

```bash
post_asset_folder: true	#修改

marked:
  prependRoot: true
  postAsset: true
```

此时再运行`hexo new post "article name"` 时，就会在`source\_posts`目录下生成md文件的同时，生成一个同名文件夹。

```bash
# 举个栗子
hexo  new post test

# source\_posts 目录下
test.md
test
```

## 本地Typora设置



为了方便 在typora 中设置如下内容  

文件 **偏好设置 图像 插入图片时 复制到指定路径** 路径默认就是在md文件目录下新建一个同名文件夹  

![img](1646215485672-c54b503b-1fcd-4ea5-899c-fbe5051c4d54.png)



习惯typora的用户，在编辑文档时，图片大多都是粘贴过来的，此时图片也会自动复制到生成的同名文件夹下。  



但如果你此时生成网页预览，会发现网页端无法显示你的图片。  



原因就是hexo的读取图片的路径和typora不一致，我们需要把图片路径从 `同名文件夹\imagename` 修改为 `imagename` 可以直接使用typora 的**Ctrl+F** 进行全局替换，将路径前缀替换为空即可。  

 

此时再生成网页就可以成功看到图片了，但在typora中并不能显示图片，因为typora中使用的相对路径找不到图片，此时需要在typora中的**格式>图片中设置图片根目录**为 md文件同名文件夹，此时你就可以在Typora中看到图片了。

![img](1646215788607-dcbd7b4b-a47b-457c-931b-597ec6f6d98b.png)

# 公式问题

首先网上很多教程说 `hexo-renderer-marked`包有问题，替换为 `hexo-renderdr-kramed`包就好了，但是有  [知乎文章](https://zhuanlan.zhihu.com/p/35668237)  说改完 `hexo-renderdr-kramed`包 会与代码高亮出现问题，因此我就没尝试，而是直接按照其所说的修改 `mark.cjs`文件

## marked.cjs 文件修改

```javascript
// \blog\node_modules\marked\lib\marked.cjs 

// escape:处替换成：

escape: /^\\([`*\[\]()#$+\-.!_>])/,

// em: 处替换成：

em: /^\*((?:\*\*|[\s\S])+?)\*(?!\*)/,
  
```

同时需要在  `theme\_config.yml` 文件中将 `mathjx`设置为true

## md文件公式修改



即使上述修改完后，md文件的公式到网页端还是会渲染出现问题，无非就是以下两个问题

- **问题1**

 `\\ \; \quad` 的渲染会出现问题 ，很容易将`\\` 识别成` \ ` `\; `识别成` ;  `渲染失败，如果公式渲染失败，可以在公式中寻找这些位置添加 `\ `

- **问题 2**

两个`{{}}  `之间要加 空格加以区分

# Reference

 [知乎 王师傅 hexo 博客如何插入图片](https://zhuanlan.zhihu.com/p/265077468)

[简书 hexo latex 换行 多行公式 终极解决方案 by 曹轩鸣](https://www.jianshu.com/p/16b7ef2653de)

[在Hexo中使用Mathjax渲染数学公式  from 张卫的博客](https://www.zhangwei.press/2021/03/03/工具/Hexo/在Hexo中渲染MathJax数学公式/)

[简书 Hexo中的LaTex公式渲染问题 by Sui_Xin](https://www.jianshu.com/p/a9f26f4cd4e6)
