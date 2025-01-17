---
typora-root-url: ./
---

## 基于 jekyll-theme-H2O 主题的个人修改

首先，感谢原博主 [xukim777](https://xukim777.github.io) 为我们提供了这么好的主题模板。

原版下载地址 [jekyll-theme-H2O](https://github.com/kaeyleo/jekyll-theme-H2O)

基础配置，参见原版配置文档

### Preview

#### [修改版在线预览 Live Demo →](http://talkcock.site/)

### 具体修改

- [添加回到顶部及底部](#添加回到顶部及底部)
- [添加分类与友情链接](#添加分类与友情链接)
- [添加关于我模块](#添加关于我模块)
- [消除双层代码高亮框](#消除双层代码高亮框)
- [添加百度统计](#添加百度统计)
- [绑定个性化域名](#绑定个性化域名)

#### 添加回到顶部及底部

博客主题作者已经将返回到顶部添加到最新的主题当中，可是该功能作者未做响应式。也就是说在手机端访问时没有这个功能的。本人懒，闲更改源代码太麻烦，就将曾经已经写好的一个回到顶部及底部的代码直接用在了博客当中。

![1](/assets/img/readme/1.jpg)

该功能简单得使用锚链接定位到相应的页面位置。

一、选择定位点

本人只想说在浏览博客的时候可以使用本功能迅速得移动到博文的顶部或者博文底部以便可以快速的切换博文以及对博文进行相关的评论。

所以，锚点就放在 **_layouts/post.html** 的相关位置。

顶部为

```html
<!-- 回到顶部 -->
<a id="gotop" name="gotop"></a>
```

底部为

```html
<!-- 回到底部 -->
<a id="gobottom" name="gobottom"></a>
```

二、编写按钮 DIV

在页面 **class="markdown-body"**之间安插

```html
<div class="go">
    <div class="box" style="font-family:'ffad_matroregular';">
        <a title="返回至顶部" class="Top" href="#gotop" target="_self">Top</a>                   	</div> 
    <div class="box">
        <a style="color: white;">---</a>
    </div> 
    <div class="box" style="font-family:'ffad_matroregular';">
        <a title="返回至底部" class="bottom" href="#gobottom" target="_self">Foot </a>
    </div>      
</div>
```

上方关于字体 **font-family** ，参见本人的博客 [前端自定义字体总结](http://talkcock.site/2018/03/05/%E5%89%8D%E7%AB%AF%E8%87%AA%E5%AE%9A%E4%B9%89%E5%AD%97%E4%BD%93%E6%80%BB%E7%BB%93.html)

三、编写按钮样式

在 **assets/css** 下新建文件，命名 **topBottom.css**

```css
.go{
	width:47px;
	height:106px;
	background-color:#272822;
	position:fixed;
	_position:absolute;
	right:12px;
	bottom:25%;
	border-radius:5px;
	z-index: 999;
}
.box a{
	text-decoration: none; 
	color: #fff;
}
.box{
	width: 100%;
	height: 33.3%;
	text-align: center;
	padding: 5px;

}
```

四、关联html与css

配置完以后，将css与post.html页面关联

在 **_includes/post-head.html** 中添加如下代码即可

```html
<!-- 返回顶部及底部 -->
<link rel="stylesheet" href="/assets/css/topBottom.css">
```



#### 添加分类与友情链接

该部分的代码编写，参考根目录下的 **tags.html**

一、分类

![1](/assets/img/readme/1.png)

源代码：到本人的[GitHub](https://github.com/zhangzhiyi0108/zhangzhiyi0108.github.io)上查看，或直接 **Fork** 我的仓库

二、友情链接

![2](/assets/img/readme/2.png)

源代码：到本人的[GitHub](https://github.com/zhangzhiyi0108/zhangzhiyi0108.github.io)上查看，或直接 **Fork** 我的仓库

链接地址需手动添加。



#### 添加关于我模块

该模块参考根目录下的**index.html**以及**tags.html**

![3](/assets/img/readme/3.png)

一、页面 **about.html** 的源码

源代码：到本人的[GitHub](https://github.com/zhangzhiyi0108/zhangzhiyi0108.github.io)上查看，或直接 **Fork** 我的仓库



二、编写 CSS 样式

本人在原 app.min.css 之中提取出有关代码并加以修改，直接在最底部添加如下代码即可

```css
.byMyself .avatar{
	width:70px;
	height:70px;
	border-radius:50%;
	margin:0 auto;
	overflow:hidden;
	box-shadow:0 1px 4px rgba(100,110,120,.53)
}

.byMyself .avatar img{width:100%}

.byMyself .sns-links{cursor:default}

.byMyself .sns-links {position:relative;display:inline-block;}

.byMyself .sns-links  a{display:inline-block}

.byMyself .sns-links  .iconfont{font-size:30px;}

.byMyself .sns-links  .iconfont{color:#b8bdc3;transition:.2s}

.byMyself .sns-links  .iconfont:hover{color:#7b848f}

/* 13个社交app图标 */
.byMyself .sns-links  .icon-weibo:hover{color:#f85555}
.byMyself .sns-links  .icon-zhihu:hover{color:#1892f5}
.byMyself .sns-links  .icon-twitter:hover{color:#39a6f8}
.byMyself .sns-links  .icon-instagram:hover{color:#d92580}
.byMyself .sns-links  .icon-juejin:hover{color:#1682fc}
.byMyself .sns-links  .icon-douban:hover{color:#2e963d}
.byMyself .sns-links  .icon-github:hover{color:#575757}
.byMyself .sns-links  .icon-facebook:hover{color:#3d5a9a}
.byMyself .sns-links  .icon-dribble:hover{color:#f26798}
.byMyself .sns-links  .icon-jianshu:hover{color:#ea6f5a}
.byMyself .sns-links  .icon-uicn:hover{color:#3498db}
.byMyself .sns-links  .icon-linkedin:hover{color:#3181be}
.byMyself .sns-links  .icon-medium:hover{color:#0be370}
```

配置完之后，即可直接使用关于我界面。



#### 消除双层代码高亮框

在原始的博客主题中有一个小Bug，就是代码高亮框出现了双层的现象。

![4](/assets/img/readme/4.png)

所以，在查看了相关源码，以及看了网上网友的建议，只需在 app.min.css 代码中进行修改即可

```css
/*将下方的 overflow: scroll; 删除即可*/
.markdown-body .highlight {
margin: 0 0 16px;
overflow: scroll;
}
```

可以使用自己的编辑器进行搜索，找到这一部分代码。修改完以后普通的框将会一层都没有。

![5](/assets/img/readme/5.png)



#### 添加百度统计

[百度统计](https://mtj.baidu.com/web/welcome/login)

在网站注册并获得源代码，将源码添加至 **_includes/head.html** 以及  **_includes/post-head.html** 之中即可。

具体不展开表述。



#### 绑定个性化域名

本人域名 [talkcock.site](http://talkcock.site) 意为：会说话的鸡

一、在阿里云或其他途径购买域名。

首先我们先买个域名,可以在[阿里云](https://cn.aliyun.com/)购买域名，买完之后登陆阿里云的管理控制台,然后点击域名，再点击解析如下

![6](/assets/img/readme/6.png)

接下来点击添加解析，并输入以下信息（记录值不一样，第一个的记录值填你的github访问地址,如`zhangzhiyi0108.github.io`,第二个填的是你的网站的ip地址，比如我原来的网站是`zhangzhiyi0108.github.io`,那么就查找`zhangzhiyi0108.github.io`的ip地址，网站的ip地址可以在这查[ip地址](http://ip.chinaz.com/)）

![7](/assets/img/readme/7.png)

然后向你的 Github Pages 仓库根目录添加一个CNAME (一定要*大写*) 文件，在CNAME里面添加你的域名信息（`不加http://`），如`talkcock.site`,并上传到你的GitHub中

等待10-20分钟之后，阿里云就会将你的域名解析到你的GitHub博客上，日后就方便使用与推广了。

------

还是那句话，关于  **jekyll-theme-H2O 主题** 的使用参考原博客博主的 **Readme** ，本人只是在修改博客之中总结了经验，方便日后使用。

不喜勿喷。