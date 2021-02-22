---
title: flex (Flexible Box弹性盒模型) 弹性布局
date: 2017-06-19
tags: [CSS, HTML, 布局]
type: 技术
---

更优雅的布局， 更多的时候我们实现功能又不仅仅是实现功能， 代码也可以更美好

<!--more-->
再之后可能是是因为这个问题真的很困扰，就有了本文要讲述的主题 Flex 弹性布局。
仿佛发现了什么不得了的事情 有木有，我就问有木有~ ~，这个必须有~
他可以由开发者自由的定义元素的排列方式, 排列顺序, 元素分布的方向, 通过拉伸缩小以适应容器的大小. 听起来都还有点小激动呢
对浏览器的支持,也还可以, 如果不是非要兼容某些不常用的老版本浏览器的话,都可以考虑用这个来布局, 简直不能更美好~~

注: 本文仅为学习记录, 参考网上提供的资料结合自己的理解和测试而成, 不考虑兼容性, 若需考虑兼容性, 再去查~ ~

## 属性
<style type="text/css">ul, li { list-style: none !important; padding: 5px; margin: 3px; }.center li { background-color: #bdcfcf; }.center li:nth-child(1) { background-color: #d3e3e6; }.center li:nth-child(2) { background-color: #c8e2de; }.center li:nth-child(3) { background-color: #87a2a0; }.center li:nth-child(4) { background-color: #85a3a0; }.center li:nth-child(5) { background-color: #7da797; }.center li:nth-child(6) { background-color: #cce7ce; }.center li:nth-child(7) { background-color: #a2bfb8; }.center li:nth-child(8) { background-color: #3d3b3b; }.center li:nth-child(9) { background-color: #798f85; }.center li:nth-child(10) { background-color: #c6c1b5; }.center li:nth-child(11) { background-color: #a18d6f; }.center li:nth-child(12) { background-color: #d7eedd; }.center li:nth-child(13) { background-color: #f9f6ec; }.center li:nth-child(14) { background-color: #f7e39d; }.center { text-align: center; color: #fff; border: 1px solid #daf7f2;} .center{width: 820px; margin: 0 auto;}</style>

### display: flex; 

声明使用弹性布局
当元素少的时候,会靠左排列(既是外层元素加了center)
<div class="center"><ul style="display: flex; "><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li></ul></div>

### display: inline-flex;
声明使用弹性布局(内联块级)
外层元素center之后会居中
<div class="center"><ul style="display: inline-flex;"><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li></ul></div>

无论是inline-flex 还是flex 当子容器内元素有很多时,全都会排在一排, 挤在一起, 若是容器本身放不下的话就会超出容器, 若是不设置flex-wrap就不换行~~
<div class="center"><ul style="display: inline-flex;"><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li></ul></div>

### flex-direction 
控制内容的显示的方向, 如下:

flex-direction:  row; 水平排列显示(默认)
<div class="center"><ul style="display: inline-flex; flex-direction:  row;"><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li></ul></div>
flex-direction:  row-reverse; 水平倒序排列显示
<div class="center"><ul style="display: inline-flex; flex-direction:  row-reverse;"><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li></ul></div>
flex-direction:  column; 垂直排列显示
<div class="center"><ul style="display: inline-flex; flex-direction:  column;"><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li></ul></div>
flex-direction:  column-reverse; 垂直倒序排列显示
<div class="center"><ul style="display: inline-flex; flex-direction:  column-reverse;"><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li></ul></div>

### flex-wrap 
控制内容是否需要换行, 如下:
flex-wrap: nowrap;  不换行 (默认, 坚决不换行,一直延伸到天际~)
<div class="center"><ul style="flex-wrap: nowrap; display: flex;"><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li></ul></div>
flex-wrap: wrap; 换行超出容器部分换行,正序显示
<div class="center"><ul style="flex-wrap: wrap; display: flex;"><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li></ul></div>
flex-wrap: wrap-reverse;  换行超出容器部分换行,倒序显示(就连没填满的缺口都显示在第一行)~
<div class="center"><ul style="flex-wrap: wrap-reverse; display: flex;"><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li></ul></div>

### flex-flow 
flex-direction和flex-wrap的合体(默认row nowrap), 如下:
多个组合, 
flex-flow: row-reverse wrap-reverse; 
<div class="center"><ul style="flex-flow: row-reverse wrap-reverse; display: flex;"><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li></ul></div>

### justify-content 
控制对齐方式, 如下:
justify-content: flex-start; 左对齐(默认);
<div class="center"><ul style=" justify-content: flex-start; display: flex;"><li>白骨夫人</li><li>唐僧骑马咚啦个咚</li><li>盘丝大仙</li></ul></div>
 justify-content: flex-end; 右对齐
<div class="center"><ul style=" justify-content: flex-end; display: flex;"><li>白骨夫人</li><li>唐僧骑马咚啦个咚</li><li>盘丝大仙</li></ul></div>
 justify-content: center; 居中对齐
<div class="center"><ul style=" justify-content: center; display: flex;"><li>白骨夫人</li><li>唐僧骑马咚啦个咚</li><li>盘丝大仙</li></ul></div>
 justify-content: space-between; 两边对其, 元素之间间隔等分
<div class="center"><ul style=" justify-content: space-between; display: flex;"><li>白骨夫人</li><li>唐僧骑马咚啦个咚</li><li>盘丝大仙</li></ul></div>
 justify-content: space-around; 单个元素两边等分, (和使用margin类似, 元素与元素之间的距离,是一个元素的边距*2)
<div class="center"><ul style=" justify-content: space-around; display: flex;"><li>白骨夫人</li><li>唐僧骑马咚啦个咚</li><li>盘丝大仙</li></ul></div>

<style type="text/css">.w li{ width: 100px; }</style>
### align-items
align-items: stretch; (默认) 全部拉伸使其和最高的元素一致
<div class="center w"><ul style="align-items:stretch; display: flex;"><li>白骨夫人, 都是白骨,虽然也是可怜的人儿,是妖怪,可是还是挺漂亮的呀</li><li>女儿国主, 女儿国之主, 说什么王权富贵,怕什么戒律清规~</li><li>嫦娥姐姐, 第一美人儿~</li><li>盘丝大仙</li><li>玉兔妹妹, 呆萌呆萌的小兔子</li><li>白面狐狸,这个真不知道是哪一集出现的了</li></ul></div>
align-items: center; 上下居中
<div class="center w"><ul style="align-items: center; display: flex;"><li>白骨夫人, 都是白骨,虽然也是可怜的人儿,是妖怪,可是还是挺漂亮的呀</li><li>女儿国主, 女儿国之主, 说什么王权富贵,怕什么戒律清规~</li><li>嫦娥姐姐, 第一美人儿~</li><li style="font-size: 20px;">盘丝大仙</li><li>玉兔妹妹, 呆萌呆萌的小兔子</li><li>白面狐狸,这个真不知道是哪一集出现的了</li></ul></div>
align-items: flex-start; 基于容器顶部对齐
<div class="center w"><ul style="align-items: flex-start; display: flex;"><li>白骨夫人, 都是白骨,虽然也是可怜的人儿,是妖怪,可是还是挺漂亮的呀</li><li>女儿国主, 女儿国之主, 说什么王权富贵,怕什么戒律清规~</li><li>嫦娥姐姐, 第一美人儿~</li><li>盘丝大仙</li><li>玉兔妹妹, 呆萌呆萌的小兔子</li><li>白面狐狸,这个真不知道是哪一集出现的了</li></ul></div>
align-items: flex-end; 基于容器底部对齐
<div class="center w"><ul style="align-items: flex-end; display: flex;"><li>白骨夫人, 都是白骨,虽然也是可怜的人儿,是妖怪,可是还是挺漂亮的呀</li><li>女儿国主, 女儿国之主, 说什么王权富贵,怕什么戒律清规~</li><li>嫦娥姐姐, 第一美人儿~</li><li style="font-size: 30px;">盘丝大仙</li><li>玉兔妹妹, 呆萌呆萌的小兔子</li><li>白面狐狸,这个真不知道是哪一集出现的了</li></ul></div>
align-items: baseline; 基线对齐(就是每个元素第一排的文字的底部位置呈一条直线)
<div class="center w"><ul style="align-items: baseline; display: flex;"><li style="font-size: 12px;">白骨夫人, 都是白骨,虽然也是可怜的人儿,是妖怪,可是还是挺漂亮的呀</li><li style="font-size: 15px;">女儿国主, 女儿国之主, 说什么王权富贵,怕什么戒律清规~</li><li  style="font-size: 20px;">嫦娥姐姐, 第一美人儿~</li><li style="font-size: 30px;">盘丝大仙</li><li>玉兔妹妹, 呆萌呆萌的小兔子</li><li  style="font-size: 18px;">白面狐狸,这个真不知道是哪一集出现的了</li></ul></div>


### align-content 
视觉上的效果呢,感觉和align-items差不多,就是他是纵向的
align-content: center; 整体上下居中对齐
<style type="text/css">.align-div {flex-flow: row wrap;display: flex; height: 350px; } .align-div ul{justify-content: space-between;  display: flex; width: 100%;}</style>
<div class="center align-div" style="align-content: center; "><ul><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li></ul><ul><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li></ul><ul><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li></ul></div>
align-content: stretch; 上下等分之后在拉伸,使其子节点高度全都相等
<div class="center align-div" style="align-content: stretch; "><ul><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li></ul><ul><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li></ul><ul><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li></ul></div>
align-content: flex-start; 基于容器顶部对齐
<div class="center align-div" style="align-content: flex-start; "><ul><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li></ul><ul><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li></ul><ul><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li></ul></div>
align-content: flex-end; 基于容器底部对齐
<div class="center align-div" style="align-content: flex-end; "><ul><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li></ul><ul><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li></ul><ul><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li></ul></div>
align-content: space-between; 使每列之间的间隔都相等
<div class="center align-div" style="align-content: space-between; "><ul><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li></ul><ul><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li></ul><ul><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li></ul></div>
align-content: space-around; 上下等分之后,再在每一行的上下居中
<div class="center align-div" style="align-content: space-around; "><ul><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li></ul><ul><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li></ul><ul><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li></ul></div>

### order
自动按照设置的值来排列位置, 数字越小越靠前
<div class="center"><ul style="justify-content: space-between;  display: flex;"><li style="order:3">order:3</li><li style="order:2">order:2</li><li style="order:1">order:1</li><li style="order:0"> order:0</li></ul></div>

### flex-grow 
放大容器中的元素(占用剩余元素, 按照flex-grow数值的多少来按比例分配)
默认为0, 剩余不占用, 若全部设置为一样的值,则均分
<div class="center"><ul style="justify-content: space-between;  display: flex;"><li style="flex-grow: 4">白骨夫人4</li><li style="flex-grow: 3">女儿国主3</li><li style="flex-grow: 1">盘丝大仙1</li></ul></div>

### flex-shrink
缩小容器中的元素(当元素过多的时候自动缩小元素的大小,以适应当前容器)
默认为1, 过多时自动缩小, 若设置为0,则不会缩小
<style type="text/css">.shrink li{flex-shrink:1}</style>
<div class="center shrink"><ul style="justify-content: space-between;  display: flex;"><li style="flex-shrink: 0">白骨夫人0</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li></ul></div>

### flex-basis
分配剩余空间(当元素有剩余空间的时候, 各自可以占有的长度,  当元素增多的时候,就会按照这个值的比例来慢慢缩小元素的大小)
可以为数值或者auto
<div class="center"><ul style="justify-content: space-between;  display: flex;"><li style="flex-basis: 200px; ">白骨夫人</li><li style="flex-basis: 300px; ">女儿国主</li><li style="flex-basis: 100px; ">盘丝大仙</li><li style="flex-basis: 100px; ">盘丝大仙</li><li style="flex-basis: 100px; ">盘丝大仙</li><li style="flex-basis: 200px; ">白骨夫人</li><li style="flex-basis: 200px; ">白骨夫人</li><li style="flex-basis: 200px; ">白骨夫人</li></ul></div>

### flex
flex-grow(放大) flex-shrink(缩小) flex-basis(分配剩余) 三者的简写形式
默认值initial = 0 1 auto 
auto =  1 1 auto; 未满时放大 溢出时缩小 剩余空间自动分配 (最常用)
none = 0 0 auto;  未满时不放大 溢出时不缩小 剩余空间自动分配
<style type="text/css"> .flex-test li{ flex: 1 1 auto;} </style>
<div class="center flex-test"><ul style="display: flex;"><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li></ul></div>

### align-self
可以为某个特定元素设置对齐方式
默认为auto 表示集成父元素的align-items 如果没有父元素等于stretch
<div class="center w"><ul style="align-items: flex-start; display: flex;"><li style="font-size: 14px;">白骨夫人, 都是白骨,虽然也是可怜的人儿,是妖怪,可是还是挺漂亮的呀</li><li style="font-size: 15px; align-self: flex-end">align-self: flex-end<br/>女儿国主, 女儿国之主, 说什么王权富贵,怕什么戒律清规~</li><li  style="font-size: 20px; align-self: center;">align-self: center<br/>嫦娥姐姐, 第一美人儿~</li><li style="font-size: 25px; align-self: baseline;">align-self: baseline;<br/>盘丝大仙</li><li>玉兔妹妹, 呆萌呆萌的小兔子</li><li  style="font-size: 18px;  align-self: stretch;">align-self: stretch;<br/>白面狐狸,这个真不知道是哪一集出现的了</li><li  style="font-size: 25px;">侍香,奎木狼守护的女子,侍香下凡后,他追随而下,共同生活了十三年~</li></ul></div>


## 实例
### 1.
<style type="text/css">.column-1, .column-2, .column-8{display: flex;}.column-1 li{flex: 1 1 100%;}.column-2 li{flex: 1 1 50%;}.column-8 li{flex: 1 1 12.5%;}</style>
<div class="center"><ul class="column-1"><li>西游记</li></ul><ul class="column-2"><li>师徒四人</li><li>妖精</li></ul><ul class="column-8"><li>唐僧</li><li>悟空</li><li>八戒</li><li>老沙</li><li>白骨夫人</li><li>女儿国主</li><li>盘丝大仙</li><li>嫦娥姐姐</li></ul></div><br/>
### 2.