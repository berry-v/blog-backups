---
title: flex (Flexible Box) 弹性布局
date: 2017-06-19
tags: [css, html, 布局]
type: 技术类
---

布局，其实不用多做解释，只能说真的很重要，不好的布局，看起来真很累呀、累呀、呀~ ~ ~自此回音回荡一万里~ ~ ~ ~
这些年，最常见的解决方案就是基于盒模型，然后用绝对定位，浮动定位什么的来解决这个问题。
其实也没什么不好，就是吧，感觉不那么灵活，然后有一些比较特殊的定位，就会超级麻烦~~
特别是，在改之前已经做好的布局的时候，那叫一个简直了，在此省略吐槽一万字~ ~ ~ 

<!--more-->
再之后可能是是因为这个问题真的很困扰，就有了本文要讲述的主题 Flex 弹性布局。
仿佛发现了什么不得了的事情 有木有，我就问有木有~~，这个必须有~

## display
<style type="text/css">ul, li { list-style: none !important; padding: 5px; margin: 3px; }.center li { background-color: #bdcfcf; }.center li:nth-child(1) { background-color: #d3e3e6; }.center li:nth-child(2) { background-color: #c8e2de; }.center li:nth-child(3) { background-color: #87a2a0; }.center li:nth-child(4) { background-color: #85a3a0; }.center li:nth-child(5) { background-color: #7da797; }.center li:nth-child(6) { background-color: #cce7ce; }.center li:nth-child(7) { background-color: #a2bfb8; }.center li:nth-child(8) { background-color: #3d3b3b; }.center li:nth-child(9) { background-color: #798f85; }.center li:nth-child(10) { background-color: #c6c1b5; }.center li:nth-child(11) { background-color: #a18d6f; }.center li:nth-child(12) { background-color: #d7eedd; }.center li:nth-child(13) { background-color: #f9f6ec; }.center li:nth-child(14) { background-color: #f7e39d; }.center { text-align: center; color: #fff; border: 1px solid #daf7f2;}</style>

以下,全都是在外层元素加了center的效果
### display: flex;

当元素少的时候,会靠左排列(既是外层元素加了center)
<div class="center"><ul style="display: flex; "><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li></ul></div>

当子元素有很多时,全都会排在一排, 挤在一起~~
<div class="center"><ul style="display: flex; "><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li></ul></div>

### display: inline-flex;

外层元素center之后会居中
<div class="center"><ul style="display: inline-flex;"><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li></ul></div>

当子元素有很多时,全都会排在一排, 挤在一起~~
<div class="center"><ul style="display: inline-flex;"><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li></ul></div>

注意，设为 Flex 布局以后，子元素的float、clear和vertical-align属性将失效

## 容器的属性
### flex-direction 控制内容的排列方向, 显示如下:

flex-direction:  row; 横向显示
<div class="center"><ul style="display: inline-flex; flex-direction:  row;"><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li></ul></div>
flex-direction:  row-reverse; 横向倒序显示
<div class="center"><ul style="display: inline-flex; flex-direction:  row-reverse;"><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li></ul></div>
flex-direction:  column; 纵向显示
<div class="center"><ul style="display: inline-flex; flex-direction:  column;"><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li></ul></div>
flex-direction:  column-reverse; 纵向倒叙显示
<div class="center"><ul style="display: inline-flex; flex-direction:  column-reverse;"><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li></ul></div>

### flex-wrap 控制内容换行
flex-wrap: nowrap;  坚决不换行,一直延伸到天际~
<div class="center"><ul style="flex-wrap: nowrap; display: flex;"><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li></ul></div>
flex-wrap: wrap; 换行,正序显示~
<div class="center"><ul style="flex-wrap: wrap; display: flex;"><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li></ul></div>
flex-wrap: wrap-reverse;  换行,倒叙显示(就连没填满的缺口都显示在第一行)~
<div class="center"><ul style="flex-wrap: wrap-reverse; display: flex;"><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li><li>白骨夫人</li><li>女儿国主</li><li>嫦娥姐姐</li><li>盘丝大仙</li><li>玉兔妹妹</li><li>白面狐狸</li></ul></div>

### flex-flow 
flex-direction和flex-wrap的合体(默认row nowrap)
flex-flow: column wrap; 试了一下,意义不大,有使用场景的时候再来补充;

### justify-content 控制对齐方式
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

## 项目属性
### order
自动按照设置的值来排列位置
<div class="center"><ul style="justify-content: space-between;  display: flex;"><li style="order:3">order:3</li><li style="order:2">order:2</li><li style="order:1">order:1</li><li style="order:0"> order:1</li></ul></div>

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
flex-grow flex-shrink flex-basis 三者的合体
默认值0 1 auto 

### align-self
可以为某个特定元素设置对齐方式
默认为auto 表示集成父元素的align-items 如果没有父元素等于stretch
<div class="center w"><ul style="align-items: flex-start; display: flex;"><li style="font-size: 14px;">白骨夫人, 都是白骨,虽然也是可怜的人儿,是妖怪,可是还是挺漂亮的呀</li><li style="font-size: 15px; align-self: flex-end">align-self: flex-end<br/>女儿国主, 女儿国之主, 说什么王权富贵,怕什么戒律清规~</li><li  style="font-size: 20px; align-self: center;">align-self: center<br/>嫦娥姐姐, 第一美人儿~</li><li style="font-size: 25px; align-self: baseline;">align-self: baseline;<br/>盘丝大仙</li><li>玉兔妹妹, 呆萌呆萌的小兔子</li><li  style="font-size: 18px;  align-self: stretch;">align-self: stretch;<br/>白面狐狸,这个真不知道是哪一集出现的了</li><li  style="font-size: 25px;">侍香,奎木狼守护的女子,侍香下凡后,他追随而下,共同生活了十三年~</li></ul></div>

