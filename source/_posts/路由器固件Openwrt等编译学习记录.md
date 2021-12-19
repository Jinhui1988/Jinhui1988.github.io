---
title: 路由器固件Openwrt等编译记录
comments: true
abbrlink: 1dpod369
tags:   
  -  路由器固件 
  -  openwrt编译 
  -  老毛子固件 
  -  固件编译
  -  padavan 
  



cover: https://img2.baidu.com/it/u=3552951702,1780455513&fm=253&fmt=auto&app=120&f=JPEG
categories: 技术
date: 2021-12-19 22:20:53
toc:
---



##  开篇：

​        这是一个openwrt编译的教过程，在b站看的教程，记录下的，所以穿上来吧，不传白不传，放哪里干吗！ 我的路由是红米AC2100，  什么是openwrt？这个是一个路由器固件，刚开始好像是华硕家的固件，下面是一个网友的开发，大致介绍了这些固件：华硕是对岸（台湾）一家电子公司大家都知道，他有很多路由器产品，而且大都也是用Linux系统开发的，开源的也很多，名字里也有WRT，所以，华硕固件就是指华硕原版固件，或者轻度改造的华硕固件. 其中，在N14U N54U 的固件上经过俄国（老毛子）大神深度开发的华硕固件，就是padavan（俗称老毛子），因为运行速度快，界面友好，对硬件要求低，入门小白用的最多，所以叫老毛子固件! 梅林是用高大上的华硕高端路由器固件再二次开发（移植）的，开发组在国外，所以是英文界面，国内的开发组在梅林基础上再开发的中文固件，添加了很多我们喜好的软件，梅林对硬件要求高，最最低64M 存储，128M内存，当然适配K2的8M 64M硬件版本也有，都是经过论坛大神精简后的，去掉了很多有用的功能，而且剩余内存太少，实际体验很差，用的人不多。所以，大家最喜欢最常用的2个固件都是来自华硕其他固件的来历一般都和openWRT有关，各有优点，可以根据喜好试用！以上是论坛上一些网友的科普！

## 步骤：

### 一 配置环境

**1.安装Ubuntu**（基于linux开发的软件，刚开始用win10内嵌的linux就好了，方便！我的是win7系统，不想升级系统，所以在VM虚拟机装了一个win10，就用的这个虚拟机装配的；对于小白不用麻烦装linux虚拟机了，安装完ubuntu后第一次启动要设置用户名和密码，不然编译不成功，密码输入的时候是看不见的，是因为linux本来就是这样的！~） 我用的是win10是LTSC2019，所以怎么下载ubuntu呢，因为不能想普通的windows安装程序那样下载就直接装，我试了下载了，但是一堆文件，不是传统意义的那种windows安装包，所以这种方法安装我就不考虑了，头疼！所以我在网上找了下，都说在windows store里下载就好，所以我就只能再下载个windows store安装包，因为LTSC版本没有windows store！**安装方法概述：** 网上找安装包就好了，这个上网搜就好，没什么可说的，有个遇到的问题是，如果下载好了打开store时，提示没有网络，那就把设置里的网络下面的proxy里的选项关掉就好！然后在里面搜索ubuntu下载就好了！然后首次启动就像上面说的设置好用户名和密码，记住就好! 还有个非常重要的点，就是编译全程一定要全局科学上网，不然必定失败！

**下面是ubuntu的科普：** Ubuntu是一个以桌面应用为主的[Linux](https://baike.baidu.com/item/Linux/27050)操作系统，其名称来自非洲南部祖鲁语或豪萨语的“ubuntu"一词，意思是“人性” “我的存在是因为大家的存在"，是非洲传统的一种价值观。Ubuntu基于[Debian](https://baike.baidu.com/item/Debian/748667)发行版和Gnome桌面环境，而从11.04版起，Ubuntu发行版放弃了[Gnome](https://baike.baidu.com/item/Gnome/5105879)桌面环境，改为Unity。从前人们认为Linux难以安装、难以使用，在Ubuntu出现后这些都成为了历史。Ubuntu也拥有庞大的社区力量，用户可以方便地从社区获得帮助。 自Ubuntu 18.04 LTS起，Ubuntu发行版又重新开始使用[GNOME3](https://baike.baidu.com/item/GNOME3/10312204)桌面环境。    



### 二 按照Github大神的代码执行

- **概述：** 

  根据github大神提供的教程，用人家的编译代码输入命令行逐步执行就好了！（中间输入自己路由的cpu架构和cpu型号以及路由的型号），如果要装插件，位置在luci -application里，自己选择就好了了！

- **Github大神提出的编译注意事项：** 

  1.**不**要用 **root** 用户进行编译！！！

  2.国内用户编译前最好准备好梯子

  3.默认登陆IP 192.168.1.1 密码     password

- **Github大神的保姆级编译代码师示范：** 

​     **初次编译：**  

​      1.首先装好 Ubuntu 64bit，推荐 Ubuntu     20.04 LTS x642.

​       2.命令行输入 sudo apt-get update ，

​        然后输入 sudo apt-get -y install     build-essential asciidoc binutils bzip2 gawk gettext git libncurses5-dev     libz-dev patch python3 python2.7 unzip zlib1g-dev lib32gcc1 libc6-dev-i386     subversion flex uglifyjs git-core gcc-multilib p7zip p7zip-full msmtp     libssl-dev texinfo libglib2.0-dev xmlto qemu-utils upx libelf-dev autoconf     automake libtool autopoint device-tree-compiler g++-multilib antlr3 gperf     wget curl swig rsync

​      3.使用 git clone https://github.com/coolsnowwolf/lede 命令下载好源代码，然后 cd lede 进入目录

​      4../scripts/feeds update     -a
​          ./scripts/feeds install -a
​          make menuconfig

​      5.make -j8 download V=s 下载dl库（国内请尽量全局科学上网）

​      6.输入 make -j1 V=s （-j1     后面是线程数。第一次编译推荐用单线程）即可开始编译你要的固件了。本套代码保证肯定可以编译成功。里面包括了 R21 所有源代码，包括 IPK 的。

​      **二次编译：** 

​      cd lede
​      git pull
​     ./scripts/feeds update -a && ./scripts/feeds install -a
​     make defconfig
​     make -j8 download
​     make -j$(($(nproc) + 1)) V=s

如果需要重新配置：

​     rm -rf ./tmp && rm -rf .config
​     make menuconfig
​     make -j$(($(nproc) + 1)) V=s

编译完成后输出路径：bin/targets

由于wsl的PATH路径中包含带有空格的Windows路径，有可能会导致编译失败，请在将make -j1 V=s或make -j$(($(nproc) + 1)) V=s改为

首次编译：

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin make -j1 V=s 

二次编译：

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin make -j$(($(nproc) + 1)) V=s

对了，如果你有安装第三方插件的需求，可以按照下面的命令：

在ubuntu输入命令make menuconfig进入编译页面（如果进不去，是忘了输入cd lede了，没有指定路径），插件都是装在luci-application里面的，接下来就是在github上找到插件的仓库地址，然后命令如下：

cd package/lean/

git clone +XXXX

cd ..

cd ..

make menuconfig

make package/lean/插件名称/compile V=s

插件名称就替换成你要装的那个插件的名字！

**注意：** 上面初次编译的第6步就是编译固件了，过程需要6个小时左右，非常慢，我编译了两次，不知道怎么回事，始终没有bin后缀的编译文件，不知道哪里出错了，如果是第一次编译，尽量不要选择太多的插件，就默认也好，先走一遍流程，尽量确保第一次成功，不然后面失败率据说有点高，第一次教程说挺重要的！我的这个就暂时不弄了，太慢了，这个文章也是写下来做个记录，不然就很快忘了！



## 总结：

​        到这里基本就是等编译结果了，如果编译结束你看代码没有出现任何ERROR的字样，那大概率可能成功了，如果出现了可能就失败了，我以为我的会成功，因为他编译了整整6个小时，结果结果中两次都带有ERROR字样，所以果不其然，根本找不到bin后缀的编译固件，其他插件等ipk文件等倒是都在，简单总结就是，第一步首先安装ubuntu，应该是模拟linux环境，然后就找github大神提供的代码逐步执行就好了，简直是保姆级教学，不过我找了老毛子固件的编译，好像没有写这么详细的，期间遇到什么命令行输入出错之类的，后来就没继续了，因为教程写的不够详细，作为小白出错率就非常高了！大致就这些内容，就当个记录，不然虽然编译了一遍，不记录估计很快就忘了！

​       

**PEACE!**

​      






​                                        

  
