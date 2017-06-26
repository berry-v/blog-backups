---
title: console 和 debugger 调试
date: 2017-06-26 18:49:33
tags: [js, 调试]
---
话说, 为什么想写这个呢, 额, 只是想起来写什么就写什么.

想当年(2013年), 刚从学校毕业还不是很明白前端是做什么, 就开始慢慢做前端, 一开始连console debugger是什么都不知道, 咳咳, 尴尬 , 不过都不重要, 现已过去好多年.
千万不要吐槽我, ~ ~ ~ 后续~ ~ 没有后续 ~ ~ ~
<!-- more -->

## debugger;
直接在代码中想设置断点的地方加上debugger; 刷新就能看到效果. 适用于同一个地方需要调试多次的时候, 毕竟写在代码中, 每次都会到调试模式.
其实我觉得这都是空话, 啥时候都可以用. 有人会觉得不如直接在浏览器上打断点, 但是有些情况呢, 他还是很实用的,具体情况具体取舍嘛.

## console(window上的对象, 用于开发环境中)
对象原型如下:
>assert : function assert()
clear : function clear()
count : function count()
debug : function debug()
dir : function dir()
dirxml : function dirxml()
error : function error()
group : function group()
groupCollapsed : function groupCollapsed()
groupEnd : function groupEnd()
info : function info()
log : function log()
markTimeline : function markTimeline()
memory : (...)
profile : function profile()
profileEnd : function profileEnd()
table : function table()
time : function time()
timeEnd : function timeEnd()
timeStamp : function timeStamp()
timeline : function timeline()
timelineEnd : function timelineEnd()
trace : function trace()
warn : function warn()

### log()
在我看来是最常用的了, 在我调试的时候, debugger和console.log()是我最常用的东西.
### assert()
根据第一个参数的true/false来决定是否抛出异常，false抛出异常并在控制台输出错误信息.
### clear()
清空控制台打印的信息, 一般在浏览器调试模式中的直接使用.
### count();
输出传入的参数以及调用的次数, 参数为字符串, 如果没有参数仅输出次数.
### debug
≈≈log() 输出的信息和log()没看出差别
### dir()
输出一个JavaScript对象的属性和属性值.
### dirxml()
### error();
输出一条错误消息, 参数可不固定, 多个会相加
### group
打印树状结构(把所有打印的信息按照树状图的形式展示出来)，会以groupEnd结束; 
>如
console.log('一');
console.group();
console.log('二');
console.log('二');
console.group();
console.log('三');
console.groupEnd();
console.log('二');
console.groupEnd();
console.log('一');

### groupCollapsed
和group用发现同, 所有打印的信息是折叠显示的
### groupEnd
结束group和groupCollapsed
### info()
输出和log相差无几, 只是前面多了一个图标.(具体应用场景不明)
### table
把数据以表格的形式输出(输出集合表格信息的时候简直完美)
### time()
启动一个定时器, 可以用来标示开始时间, 然后计算出一个操作占用的时长, 和timeEnd()配合使用, 当使用当前参数书调用timeEnd()时, 输出他们的毫秒差值(即计时器所记时间)
### timeEnd()
配合time()使用
### warn()
输出一条警告信息

以下,  还未察觉具体应用场景(有具体应用了之后再补充):
profile
profileEnd
timeStamp
timeline
timelineEnd
trace()
markTimeline
memory