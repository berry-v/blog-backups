---
title: web页面中图标使用 fontIcon
date: 2017-06-17
tags: [小技巧, css]
---

在制作web页面的时候，使用图标的情形是很多的，实现的方式也可以有多种。
从使用背景图片到图标字体库再到定制图标字体，虽然已经有很多人写过这个问题，但是还是想说再来简单的总结一下。


## web页面中图标使用 fontIcon

### 背景图片

不知道在多久以前还是直接用图片背景的方式来显示图标，且不说这个的利弊，就是写这一段的样式都是很多的，好处在于，可兼容低版本的浏览器。
这种方式还有很多不推荐的原因：
很多张图片的时候又增加了许多http请求，把所有的图片放到一起的时候，是减少了http请求，但是图片缩放的时候又会很不方便。
放大缩小的时候很可能会失真，体验不太好。
要是需要在不同状态下显示不同的颜色的话有需要多去处理一套图片，总之就是太麻烦了，太麻烦了，太麻烦了，重要的话要说三遍。
还有就是在样式处理的时候写的比起其他的方式稍微有点多，渐渐地也就很少有在用了。

### 图标字体库

使用已经提供好的字体图标库显示你所需要的图标，图库很全，想要的大多都能找得到。
一般会有许多不需要的图标在下载的库当中。总是觉得有点不是那么完美。
之后有一段时间也是在用这个，就是觉得只为了没几个图标就加载那么大一堆，表示有点痛心啊，痛心啊，痛心啊~
再后来，也放弃了~
如下几个图标字体库：
[fontawesome](http://fontawesome.io/)
[mfglabs-iconset](http://mfglabs.github.io/mfglabs-iconset/)
[ligature_symbols](http://kudakurage.com/ligature_symbols/)
[openwebicons](http://pfefferle.github.io/openwebicons/)
[maki-icons](https://www.mapbox.com/maki-icons/)
[typicons](http://typicons.com/)

### 自定义图标字体

很多网站都可以处理，把想要的图标转成字体文件后可以直接下载，要多少就下多少，不多不少，还可以上传自己的图标然后生成。
还可以很方便地改变图标的颜色，大小。
个人是很喜欢这种做法，只保留有用的东西~~
如下几个图标字体制作网站：
[iconfont](http://www.iconfont.cn/)
[fontello](http://fontello.com/)
[icomoon APP](https://icomoon.io/app/)

下载后的使用方法，相信大家都是知道的，下载的文件中也有使用的例子。

还有童鞋的喜欢自己去用工具生成图标来使用比如AI什么的，也是不错的，不过我不会，哈哈哈~~~

### 此处有小技巧

当我们在使用字体图标的时候一般的用法是
>@font-face {
 font-family: “icon”;
 src: url(‘./icon.eot?t=1495901382263’); / IE9/
 src: url(‘./icon.eot?t=1495901382263#iefix’) format(‘embedded-opentype’), / IE6-IE8 /
 url(‘./icon.woff?t=1495901382263’) format(‘woff’), / chrome, firefox /
 url(‘./icon.ttf?t=1495901382263’) format(‘truetype’), / chrome, firefox, opera, Safari, Android, iOS 4.2+/
 url(‘./icon.svg?t=1495901382263#icon’) format(‘svg’); / iOS 4.1- /
}
.icon {
 font-family:”icon” !important;
 font-size:16px;
 font-style:normal;
 -webkit-font-smoothing: antialiased;
 -moz-osx-font-smoothing: grayscale;
}

为每个图标创建一个class
很长一段时间是这么用的，应该也是最常用的方式吧，至少现在看到的更多的都是这么做的
>&lt;ul&gt;
	&nbsp;&lt;li&gt;&lt;i class=”icon icon-length”&gt;&lt;/i&gt;&lt;/li&gt;
	&nbsp;&lt;li&gt;&lt;i class=”icon icon-arrow-right”&gt;&lt;/i&gt;&lt;/li&gt;
	&nbsp;&lt;li&gt;&lt;i class=”icon icon-area”&gt;&lt;/i&gt;&lt;/li&gt;
	&nbsp;&lt;li&gt;&lt;i class=”icon icon-volume”&gt;&lt;/i&gt;&lt;/li&gt;
	&nbsp;&lt;li&gt;&lt;i class=”icon icon-weight”&gt;&lt;/i&gt;&lt;/li&gt;
	&nbsp;&lt;li&gt;&lt;i class=”icon icon-temperature”&gt;&lt;/i&gt;&lt;/li&gt;
	&nbsp;&lt;li&gt;&lt;i class=”icon icon-speed”&gt;&lt;/i&gt;&lt;/li&gt;
&lt;/ul&gt;
.icon-length:before { content: “\e601”; }
.icon-arrow-right:before { content: “\e602”; }
.icon-area:before { content: “\e603”; }
.icon-volume:before { content: “\e604”; }
.icon-weight:before { content: “\e605”; }
.icon-temperature:before { content: “\e606”; }
.icon-speed:before { content: “\e608”; }

使用 data- 属性来嵌入自定义数据*
后来发现还可以这样用，简直觉得神奇有木有，当有很多个图标的时候，这样写感觉会清新很多啊
>&lt;ul&gt;
	&lt;li&gt;&lt;i class=”icon” data-icon=”&amp;#xe601;”&gt;&lt;/i&gt;&lt;/li&gt;
	&lt;li&gt;&lt;i class=”icon” data-icon=”&amp;#xe602;”&gt;&lt;/i&gt;&lt;/li&gt;
	&lt;li&gt;&lt;i class=”icon” data-icon=”&amp;#xe603;”&gt;&lt;/i&gt;&lt;/li&gt;
	&lt;li&gt;&lt;i class=”icon” data-icon=”&amp;#xe604;”&gt;&lt;/i&gt;&lt;/li&gt;
	&lt;li&gt;&lt;i class=”icon” data-icon=”&amp;#xe605;”&gt;&lt;/i&gt;&lt;/li&gt;
	&lt;li&gt;&lt;i class=”icon” data-icon=”&amp;#xe606;”&gt;&lt;/i&gt;&lt;/li&gt;
	&lt;li&gt;&lt;i class=”icon” data-icon=”&amp;#xe608;”&gt;&lt;/i&gt;&lt;/li&gt;
&lt;/ul&gt;
 [data-icon] :before{
&nbsp;content: attr(data-icon);
}

最后,一排图标飘过~ ~ ~

<style type="text/css">@font-face{font-family:"icon";src:url('../assets/fonts/mengmengda/icon.eot');src:url('../assets/fonts/mengmengda/icon.eot#iefix') format('embedded-opentype'),url('../assets/fonts/mengmengda/icon.woff') format('woff'),url('../assets/fonts/mengmengda/icon.ttf') format('truetype'),url('../assets/fonts/mengmengda/icon.svg#icon') format('svg');}.icon_lists li{font-family:"icon"!important;font-size:30px;font-style:normal;-webkit-font-smoothing:antialiased;-webkit-text-stroke-width:0.2px;-moz-osx-font-smoothing:grayscale;list-style:none !important; display: inline-block;}.icon_lists li:before{content:attr(data-icon);}</style>
<ul class="icon_lists"><li data-icon="&#xe6a4;"></li><li data-icon="&#xe6a5;"></li><li data-icon="&#xe6a6;"></li><li data-icon="&#xe6a7;"></li><li data-icon="&#xe6a8;"></li><li data-icon="&#xe6a9;"></li><li data-icon="&#xe6aa;"></li><li data-icon="&#xe6ab;"></li><li data-icon="&#xe6ac;"></li><li data-icon="&#xe6ad;"></li><li data-icon="&#xe6ae;"></li><li data-icon="&#xe6af;"></li><li data-icon="&#xe6b0;"></li><li data-icon="&#xe6b1;"></li><li data-icon="&#xe6b2;"></li><li data-icon="&#xe6b3;"></li><li data-icon="&#xe6b4;"></li><li data-icon="&#xe6b5;"></li><li data-icon="&#xe6b6;"></li><li data-icon="&#xe6b7;"></li></ul>

各有利弊，具体情况，还是要根据具体使用情况去判断。
不知有无更好解决方案，有再更新~~
