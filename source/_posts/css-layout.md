---
title: 总结 CSS 布局方式
date: 2018-04-18 11:57:47
tags: [css, 布局]
---

一些css布局示例

<!-- more -->
一、有俩div， 左边固定宽度， 右边自适应
```html
<div class="content">
  <div class="left">Left</div>
  <div class="right">Right</div>
</div>
```
flex
```css
.content{
  display: flex;
  height: 100%;
}
.left{
  width: 200px;
  border-right: 1px solid #333;
}
.right{
  flex:1;
}
```
float
```css
.left{
  float: left;
  width: 200px;
  border-right: 1px solid #333;
}
.right{
  margin-left: 200px;
}
```
position
```css
.left{
  position: absolute;
  width: 200px;
  border-right: 1px solid #333;
}
.right{
  margin-left: 200px;
}
//同理， .right使用position也可
```

二、有一div， 水平垂直居中
```html
  <div class="content">
    <div class="center">Center</div>
  </div>
```
display:flex
```css
.content{
  display:flex;
  justify-content:center;
  align-items: center;
  height: 100%;
}
.center{
  border: 1px solid #999;
}
```
position: absolute
```css
.content{
  position: relative;
  height: 100%;
}
.center{
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  border: 1px solid #999;
}
```
```css
.content{
  position: relative;
  height: 100%;
}
.center{
  position: absolute;
  top: 50%;
  left: 50%;
  margin: -50px auto auto -50px;
  border: 1px solid #999;
  width: 100px;
  height: 100px;
}
```
```css
.content{
  position: relative;
  height: 100%;
}
.center{
  position: absolute;
  margin: auto;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  border: 1px solid #999;
  width: 100px;
  height: 100px;
}
```
同position:absolute一样， position:relative也同样可以使元素居中， 且有多种方法
思路基本同position:absolute一样， 比如：
```css
.content{
  height: 100%;
}
.center{
  position: relative;
  width: 100px;
  height: 100px;
  top: 50%;
  left: 50%;
  border: 1px solid red;
  transform: translate(-50%, -50%);
}
```
