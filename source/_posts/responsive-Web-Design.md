---
title: 关于响应式布局的一些总结
date: 2017-06-22
tags: [CSS, HTML, 响应式] 
---

很久以前都想写这么一篇文, 记录一下在这么多年所遇到的一些关于布局的总结, 主要是想存个档, 之后好找~~
没有多余的废话想说,嗯~ ~ ~天气真好啊~ ~ ~

<!-- more -->
## 使用rem
### 借助js控制html标签的font-size 

浏览器默认font-size是16px , 在html的font-size还没有初始化的时候1rem=16px
此时如果要默认是1rem=10px的话就应该是10/16*100%=62.5%(一般定义为62.5%是为了好计算,可以直接除以10就好了)
在不同浏览器适配的时候,可以改变 &lt;html&gt; 标签的font-size来达到用了rem的内容的变换.

以一个尺寸作为标准,之后可以自行计算(如基于640设计图)
>document.documentElement.style.fontSize = 20 * (document.documentElement.clientWidth / 320) + 'px';

宽度/320 既是媒体宽度和设计图的比例(因为一般的设计图是针对320px宽度的大小来制作的设计图(通常有640和750))
*20是因为1rem=20px (320的基准字体大小是10px的话640就应该是20px)
省略之后为
>document.documentElement.style.fontSize = document.documentElement.clientWidth / 16 + 'px';

### 用媒体查询(@media)控制html标签的font-size
除了上述方法,还可以用媒体查询来控制html的font-size. 为不同阶段的分辨率分别设置html的font-size, 可以完全不用js
@media的常用语法:
min/max-device-width/height 整个设备的显示区域
min/max-width/height 目标(如浏览器/某个应用)显示区域
>@media screen and (min-width: **px) {} //宽度大于等于某个值时使用
@media screen and (min-width: **px) and (max-width: **px) {} //宽度在某两个值之间时
@media screen and (max-width: **px) {} //宽度小于等于某个值时使用

<!-- 还有关于
基本媒体分辨率一览 
<table>
	<tr>
		<td></td>
	</tr>
</table>
-->
### 可以使用 scss 计算
(可以选择其他的,怎么方便怎么来,只是说一下实现的方法)
$ratio等于40是因为,一般的设计是根据320px宽度的大小来制作的640px的设计图
由于之前在js中定义的是20px=1rem
所以,假如我们在和媒体一样的尺寸的设计图上获取到的数据为Xpx时,他就应该是X除以20结果就是最后的rem值,
但是设计图(640)和基准媒体宽度(320)又相差了一倍,
所以,当我们在计算640设计图时需要再除以二结果就是 X/20/2=X/40

scss中自然为
>$ratio: 40;
@function fun-rem($args) { @return $args/$ratio+rem; }

同理,如果设计图是750的话
>$ratio: 40*(750/640);
@function fun-rem($args) { @return $args/$ratio+rem; }

这样使用的话,就可以直接传入设计的尺寸, 不用自己去计算, 省时省力 ~ ~ ~


