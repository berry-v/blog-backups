---
title: 对NodeList的理解
date: 2017-06-21 18:48:42
tags: [JavaScript]
---

写此文的初始原因是因为一场有对有错的争论开始的, 关于一场获取子节点返回的值的类型的争论~ ~ ~
开始的时候我认为是一个array集合, 却发现array的对象方法都不能使用, 后来看到他的类型发现他并不是一个数组~
所以以此文,总结一下.

### 为什么NodeList不是数组:
开始的时候我log()出来是[xx, xx, xx]这种形式的, 于是就以为是array类型的,但是在看返回结果的原型的时候发现array的特有方法它却没有,果然还是太年轻, 太傻太天真~~
<style type="text/css">.proto{display: flex; padding: 10px; border: 2px solid #daf7f2;} .proto li{list-style: none !important;} .proto h4{margin: 0;}</style>
<ul class="proto"><li style="flex: 1 1 auto;"><h4>Array 的原型大概是这样的</h4>concat : function concat()
	constructor : function Array()
	copyWithin : function copyWithin()
	entries : function entries()
	every : function every()
	fill : function fill()
	filter : function filter()
	find : function find()
	findIndex : function findIndex()
	forEach : function forEach()
	includes : function includes()
	indexOf : function indexOf()
	join : function join()
	keys : function keys()
	lastIndexOf : function lastIndexOf()
	length : 0
	map : function map()
	pop : function pop()
	push : function push()
	reduce : function reduce()
	reduceRight : function reduceRight()
	reverse : function reverse()
	shift : function shift()
	slice : function slice()
	some : function some()
	sort : function sort()
	splice : function splice()
	toLocaleString : function toLocaleString()
	toString : function toString()
	unshift : function unshift()
	Symbol(Symbol.iterator) : function values()
	Symbol(Symbol.unscopables) : Object</li><li style="flex: 1 1 auto;"><h4>NodeList 的原型大概是这样的</h4>entries : function entries()
	forEach : function forEach()
	item : function item()
	keys : function keys()
	length : (...)
	values : function values()
	constructor : function NodeList()
	Symbol(Symbol.iterator) : function values()
	Symbol(Symbol.toStringTag) : "NodeList"
	get length : function ()</li></ul>
不难看出, NodeList的方法还是挺少的.

### 遍历NodeList
如果我们想要遍历一个NodeList对象的话, 可以循环它的长度, 再根据长度去取值.
for(var i = 0; i< nodeList.length; i++){......}
不能使用for...in或者for each ...in 因为他会去遍历当前对象的方法
如下:
>&lt;ul id="ul-test"&gt;
&nbsp;&nbsp; &lt;li class="li-1"&gt;&lt;/li&gt;
&nbsp;&nbsp; &lt;li id="li-2"&gt;&lt;/li&gt;
&nbsp;&nbsp; &lt;li&gt;&lt;/li&gt;
&nbsp;&nbsp; &lt;li&gt;&lt;/li&gt;
&nbsp;&nbsp; &lt;li&gt;&lt;/li&gt;
&lt;/ul&gt;
var result = ''; 
for(var i in document.querySelectorAll("#ul-test li")) {
&nbsp;&nbsp; result = result + i + ', ';
}
console.log(result);

结果是 0, 1, 2, 3, 4, length, item, keys, values, entries, forEach

### 出现NodeList对象的场景. 
使用如下方法后返回的子节点列表~ ~
	Node.childNodes
	document.querySelectorAll()
	document.getElementsByName()
	...

### NodeList对象的方法:
length: 返回节点个数,
item:  返回指定节点个数
	

### 实时\非实时:
Node.childNodes返回的NodeList结果
一个实时集合, 当节点发生变化时nodeList也会随即发生改变
document.querySelectorAll返回的NodeList结果
MDN上描述了, 在多数情况下, NodeList对象是一个实时集合(即文档中的节点树发生变化,那么已经纯在的NodeList对象也可能会变化)
如Node.childNodes 是实时的
然而在某些情况下NodeList是静态的(即文档中节点树发生变化, 已经纯在的NodeList对象也不会改变)
如document.querySelectorAll 是静态的

### 像数组一样使用
如果在某些场景下需要像使用数组的一样去使用NodeList
##### 使用call
var arr = Array.prototype.slice.call(NodeList);// IE 问题
arr既是一个array类型的数组, 此时就可以使用array的方法
##### es6
var arr = Array.from(NodeList)
