---
title: Zotero教程—PC端文献与IPAD 同步
top: false
cover: false
toc: true
mathjax: true
summary: Zotero教程—PC端文献与IPAD 同步
tags:
  - 软件教程
  - 文献管理
categories: 软件
typora-root-url: ST-wx02
abbrlink: 40192
date: 2022-03-02 19:58:42
password:
coverImg:
---



之前小冰给果壳er们对比评测过相关文献管理软件的对比评测，对比下来，Zotero简约的设计、功能的可拓展性吸引了小冰，因此小冰决定使用Zotero作为文献管理软件。IPad作为文献阅读神器，一直深受使用者的热爱，但IPad端与PC端（Win）的文献同步一直困扰着不少用户。本次推送小冰就来讲解PC端文献和IPAD同步的实现。

Zotero与IPad同步实现是基于坚果云的同步、Zotfile插件的软链接进行实现。

### 太长不看系列



![img](v2-edf540e026d4a8097fd07fffbf311a20_r.jpg)



**Zotero：**

编辑>首选项>高级>文件和文件夹 **链接附件的根目录**设置为坚果云的同步文件夹。

**ZotFile插件**

**Zotero>工具>ZotFile Preferences>General Settings**中设置Location of FIles为上面设置的目录

坚果云授权PDF Expert，PDF Expert加入坚果云连接 或者直接使用PDFViewer查看坚果云文件

## 1 准备阶段

- **坚果云**

[坚果云官网](https://www.jianguoyun.com/)

注册账号 ，PC端客户端 IPAD客户端（避免出现问题）下载安装

- **Zotero** PC端客户端下载安装注册账号
- **ZotFile插件**

[Advanced PDF management for Zoterozotfile.com/](http://zotfile.com/)

PC端下载安装

- **PDF Expert** IPad客户端免费版

## 2 Zotero设置

### 01 编辑>首选项>同步

**确保文件同步都不勾选**

*这里的文件指的是文献题录信息的附件，PDF、笔记等，本次同步借助ZotFile的软链接，无须借助Zotero自身的云空间和WebDev进行同步。同时Zotero的云空间只有300M的云空间，因此没有必要将PDF等文件存储到Zotero云空间。*

![img](v2-d1e76039e2cf2c71eeb95d4fc45f075b_r.jpg)

### 02 编辑>首选项>高级>文件和文件夹。

这里需要设置一个文件目录：链接附件的根目录，**链接附件的根目录**要设置为坚果云的同步文件夹。

![img](v2-99ee13cece345650d54365d9d6f27c40_r.jpg)



***链接附件的根目录\****是文献链接附件的实际位置，当Zotero寻找链接附件时，会将该目录作为根目录，直接在该目录下寻找。举个栗子，两台电脑、一个Zotero账号，分别设置了根目录，D:\附件目录 与D:\Data\附件目录，两个根目录不同，但Zotero寻找和保存链接附件时，会直接在根目录下寻找文件。现在你可能明白了，这个根目录的设置就是为了满足不同电脑之间的同步问题，避免找不到链接附件。*

*还有一点需要注意，链接附件和附件并不是一类，刚才仅仅设置的是链接附件的根目录。我们直接拖动到Zotero的文件是普通附件，链接附件的生成需要借助ZotFile插件。*



![img](v2-b2b4be641ece228fd5ec9eddcab43af6_r.jpg)



*你可能还注意到有一个数据存储位置，这个文件夹里存储着Zotero的一些配置文件和数据等，同时所有题录文献的文件都在这个文件夹里的storage文件夹下。每一条Zotero都会创建一个随机文件夹，记录相关数据。*

*这个文件夹可以选择默认，也可以进行自定义，这个对同步不会有影响。由于Zotero会为每一条题目建一个文件夹，并对文件夹进行随机重命名，因此这样找起来文献会很麻烦，因此直接利用坚果云对该文件夹下的Storage文件夹同步并不现实。*



![img](v2-d92ea0d2bbfe13bd1a13fb1eb970e01a_r.jpg)

![img](v2-952090522a52b37cb62b3da3262126f6_r.jpg)



## 3 ZotFile 安装、使用

在ZotFile网站下载后会得到一个xpi文件，在Zotero中选择**工具>插件>齿轮图标>Install Add-on From FIle**,选择下载的xpi文件，即可导入ZotFile插件完成安装。

![img](v2-eba82fd37b45fe6e7ae8a5e31a8cc24a_r.jpg)

成功安装ZotFile插件后，在**Zotero>工具>ZotFile Preferences>General Settings**中设置Location of FIles文件目录，这个文件目录要与之前设置的**Zotero链接附件的根目录**保持一致。同时也要注意，该文件目录需要是坚果云的同步文件夹。

![img](v2-4b2242cf3883c28fea50a5dd0581173b_r.jpg)



上述配置完成后，选中文献条目（支持多选），**右键>Manage Attachments>Rename Attachments**，稍等片刻，在设置的文件夹中就出现了该条目的文献附件。如果此时打开了坚果云，即可将文献附件全部同步到云端。



![img](v2-590f019e183647761603ea14fb084285_720w.jpg)



### 文献探测

*可能果壳er们也注意到了ZotFile设置中General Settings中还有一个文件目录 Source Folder for Attaching New Files，当有新文件添加到这个文件夹里，就可以利用ZotFile插件的Attach New File功能将文件识别并进行同步。*



![img](v2-ccc70761159bb86a5f3c6037aa4b0818_r.jpg)



### 子文件分类

*如果想要将Zotero的文献利用ZotFile同步时按照Zotero界面中的文件夹层次同步，那么需要在General Settings中勾选Use subfolder defined by前的按钮，并在方框中填入* ***/%c\****。*



![img](v2-ac3a5a28ab03a10593af461437fb3ac0_r.jpg)



### 文件重命名格式

*ZotFile对文件的重命名规则在ZotFile****设置界面>Renaming Rules\****中，如果没有特殊要求选择默认就好，也可以自己进行设置，设置界面有对符号的说明，更加详细的说明可以参照官网，小冰这里就不做过多讲解了。*



![img](v2-c32810d2eac964c78262e59525fd1ed3_r.jpg)



## 4 PDF Expert 与坚果云同步

通过上述设置，完成了PC端到云端的文献同步，接下来，完成IPad端到云端的同步。

如果你并没有对PDF Expert形成依赖，可以选择**PDF Viewer**软件直接访问坚果云文件，不必进行如下的配置，只需要在**IPAD端下载安装PDF Viewer和坚果云两个软件即可。**

**以下为PDF Expert阅读坚果云文献的方法**

打开坚果云官网

[坚果云免费个人网盘注册|个人云盘|网络存储盘www.jianguoyun.com/d/home#/](https://www.jianguoyun.com/d/home#/)

完成登录，右上角点击**账户信息>安全选项>添加应用**，名称按照自己的喜欢输入即可，点击生成密码，即可获得授权密码。



![img](v2-77d224090a47700e572090e32aae33cf_r.jpg)

接下来在IPad端打开PDF Expert点击**添加连接>WebDAV**，**标题**输入自己喜欢的名称，**URL**输入坚果云服务器地址，密码输入刚才坚果云网站生成的密码。



![img](v2-d7fd0b663ebbd70f830eb355b4c59d6e_r.jpg)



如果遇到**服务器连接**问题，iPad可以 下载坚果云客户端并进行登录，重新添加应用并进行PDF Expert添加WebDAV。

添加成功后，恭喜你，你已经成功完成了PC端和IPad端的文献同步。只要有网络，IPad端就可以将PDF标注上传云端，PC端也可以随时查看标注信息。屏幕前的果壳er们快去尝试一下吧。

当然果壳er们也可以在IPad端选择其它PDF阅读器，前提是该应用支持WebDAV的添加，同样你也可以使用其它同步盘进行同步，不过国内还是坚果云比较方便。

## 5 注意事项

**不要在IPad端点击同步**。为了避免出现IPad端本地文件和PC端本地文件没有及时上传导致云端差别而发生错误的情况，建议IPad只在云端对PDF文件进行标注工作，即通过第三方应用程序（PDF Expert）的WebDAV入口直接查看PDF文件，没有必要点击文献设置中的同步按钮。

如果点击同步按钮，会将云端的文件下载到IPad本地，这样下次标注可能需要再次点击同步才能将修改的信息同步到云端，但如果PC端同时进行了修改，这样很可能会出现文件有差别而发生错误。



![img](v2-d4e1366e63885fdeab81de6e4a3e48d2_r.jpg)
