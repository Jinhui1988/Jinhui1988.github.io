
 # 个人搭建Hexo博客步骤总结


##  开篇：

​        个人搭建了一个hexo框架的个人博客，放在github上，用的主题是butterfly，刚搭建完，所以大致把重点和问题写下，我只是记录下，所以不会往细了写，以后自己回顾能看懂就好！   

## 步骤：

### 一 配置环境

**1.安装git**（点击进入[Git官网](https://git-scm.com/downloads)，如果嫌下载慢自行百度解决~） 

**2.Git与远程库进行\**SSH授权\****(点击查看教程[Git的安装-与远程仓库GitHub配置](https://www.cnblogs.com/wy0526/p/13068373.html))****

**2.安装node.js** （点击进入[nodejs官网](https://nodejs.org/zh-cn/)直接下载）（我电脑是win7，最新的node是不适配的，最后下载了V12版本）,

以上是电脑运行环境的配置，由于**node.js**是hexo框架的编译语言，所以一定得安装这个，不然hexo无法运行。

### 二 搭建博客

- 观看B站codesheep的视频一步一步走的，搭建了一个初步的butterfly主题网站，先在本地预览，**localhost:4000**端口上，后续再推到了github上，就一步一步做，也没什么可说的，他的视频地址：[codesheep](https://www.bilibili.com/video/BV1Yb411a7ty?spm_id_from=333.1007.top_right_bar_window_history.content.click)，以后如果可用，可以看下！
- 这里主要是在本地搭建完，在本地预览后，部署到github上，这个是部署的概念，主要的命令就是hexo的命令，有hexo clean，hexo g，hexo s，最后在hexo d，d之后就会部署到github上，但前提是你得安装了git工具，以及你的github账号和本地已经有ssh的秘钥授权，不然是个电脑都能和github链接，那岂不是有安全问题了？就还是以上的配置环境那一节的内容！这里暂时没有把博客源码push到github的必要，一个是部署博客，只把生成的public文件夹的东西上传到github，文件非常小，只有十几兆，而把博客源码备份到github上，是需要用的git命令，主要有，**git init，git add . , git commit -m "", git branch -M main**, 以及**git remote add origin 你的仓库url（shh或者http都可以）**，最后，**git push -u origin main**,就成功把代码备份到github上了！**这里遇到问题:**  我看教程说如果本地的代码丢了的话，可以把github的克隆下来继续用，但是我操作的时候，每次到hexo g的时候都出现问题，第一次出现说**Unknown block tag: gellary**，说什么第2列第4行有问题，这是我的相册，不能删除，第二次遇到的问题还是hexo g以后，提示错误，具体是：**Warn No Layout: Index.html**，意思是可能缺少这个html文件？所以也就中断在这里了，后续本地预览也没有成功实现。**具体克隆到本地的命令大概是:** 以上说的前提都是要装上面的运行环境下才能实现，在你想克隆的盘符里，shift右键点击启用cmd，输入**git clone **你的仓库url，然后回车，就克隆下来了，接着到克隆下载的文件夹路径里，安装**npm install**，安装下这个他会生成**node_modules**的文件夹，应该是hexo运行需要的环境，然后再**hexo g**生成以下，**hexo s**启用下，如果一切顺利，就能在localhost:4000端口里看到你的博客了，我正式卡在了hexo g这一步骤，看代码里有出错，所以没法进行余下的操作，**这个问题需要注意，以后克隆到本地肯定用用到，无论是代码还是这个博客的代码修改，需要注意。**
- 博客配置的事项和具体的东西，主要是看了官方文档和B站两个视频教程，[B站up视频教程的链接](https://www.bilibili.com/video/BV1fw41197NS?spm_id_from=333.1007.top_right_bar_window_history.content.click)，[官方作者文档的链接](https://butterfly.js.org/posts/21cfbf15/)，[还有个B站的up链接是](https://www.bilibili.com/video/BV1zo4y1U7aC?spm_id_from=333.1007.top_right_bar_window_history.content.click)，主要就是看了这几个，特别是第一个up，他出了很多集！配置之类的，一步一步走就是了！第三个up把他的源码放出来了，所以我下载了下来，看了下他音乐的链接是怎么放的，我音乐的插件之前不知道怎么弄，一直在页面出不了音乐！他用的网易云，我最后把我的spotify歌单的链接拿出来放在了主题的配置文件里，可能是会员，所以能听，如果不是会员，可能只能试听片段，不知道没有会员的人上我的博客能不能听到完整的音乐！！！
- 配置差不多了后，就可以远程部署到github上了，就是上面2里说的步骤，当然之后搜索引擎收录啊之类的事情，看第一个up的教程走就好了！博客部署好后，就把自己的源码也备份到github上，方便一会本地丢失，还能在github上找到，**当我把我本地源码部署到github的时候还有问题：** 就是我的butterfly主题文件里的配置都没有备份到github，后来了解了下，可能是github的原因，因为我用的butterfly主题也是在github官方人员的仓库了，所以github默认是不上传这个的？   对了，照着第一个up的教程在github上搭建了一个免费的图床，可以把图片传上去，又加了个imgbot的插件，可以自动优化上传的图片体积，这个搭建图床是配合picgo软件来上传的，只要设置和端口以及仓库名字就可以！！

## 总结：

​        用到的东西就是git工具，以及node.js包，用来支持hexo框架，然后就是选择一个自己喜欢的主题皮肤文件，主题皮肤文件的链接是：（[Themes | Hexo](https://hexo.io/themes/)），这里面可以随意找你喜欢的主题，然后点击它，找到他在github的链接，在本地用git clone的命令加上他的链接，就能自动拷贝到我们本地博客根目录的主题文件夹了！然后及时找以上的教程配置，改代码之类就可以了！添加功能，不如说加个说说，得要配置LeanCloud账号，然后在里面建立新的应用class，[配置LeanCloud教程](https://artitalk.js.org/doc.html#%F0%9F%8C%88-leancloud-%E7%9A%84%E7%9B%B8%E5%85%B3%E5%87%86%E5%A4%87)，再加个留言区，留言区用的是valine，也可以在LeanClould注册一个，获取他的appID和appkey就好了，上面的加说说，也是在LeanCloud里申请appid和appkey，然后填在博客根目录的_config配置文件里？或者在主题的配置文件里，教程链接是：[Valine配置](https://valine.js.org/quickstart.html)。其他的功能自己想要可以看官方文档，比如改top img之类的，比如在每个index.md文件里放个cover：img url，这样你发这篇文章时候，封面图就是你新设置的图片，不然都是默认的，一样不好看！

​       

## 说明：

​       暂时就想到这些，后续有新的问题，再p上来吧！方便以后看下！这波搭建博客以及使用git，初步使我了解了git工具的使用，以及如何备份到github以及如何再克隆到我的本地修改然后再上传，感觉还是挺方便的！ 由于是我的笔记和大致步骤总结，所以不会详细说，希望见谅！！！！有什么建议，可以在评论区留言哦！！！！





**PEACE!**

​      






​                                        

  
