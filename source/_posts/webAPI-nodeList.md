---
title: 对NodeList的理解
date: 2017-06-21 18:48:42
tags: [JavaScript]
---

写此文的初始原因是因为一场有对有错的争论开始的, 关于一场获取子节点返回的值的类型的争论~ ~ ~
开始的时候我认为是一个array集合, 却发现array的对象方法都不能使用, 后来查询资料发现他并不是一个数组~

所以以此文,总结一下.

首先, 出现NodeList对象的场景是使用了 document.querySelectorAll 和 Node.childNodes 之后返回的子节点列表

