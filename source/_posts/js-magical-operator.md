---
title: 神奇的运算符
date: 2017-07-27
tags: [小技巧, JavaScript]
---

话说， 以前一直以为运算符也就应用于， 判断啊， 计算啊，什么的～ ～ ～ 也没想过还能有更多很实用又美腻的写法，  直到后来， 看了别人写的代码～ ～ ～
所以呀， 看别人写的代码还是很有必要的。哇咔咔咔咔咔咔咔咔咔咔
<!-- more -->

## 阿啵呲嘚
&& 当&&之前的条件为 true 时执行&&之后的代码。
|| 当||之前的条件为 false 时执行&&之后的代码。
二者， 恰好相反

## &&
### 用于简短的判断 
```python
  let name = document.getElementById('name');
  name && clearValue(name); // 条件为真 方法执行
  function clearValue(input){
    input.value='';
  }
```

## ||
### 判断变量是否定义， 没有定义则赋一个初始值
var num = num || 0;

## || & &&
### 简化switch
```python
  let condition = Math.ceil(Math.random()*5), color;
  switch (condition) {
    case 0:
      color = '红艳艳';
      break;
    case 1:
      color = '黑乎乎';
      break;
    case 2:
      color = '黄灿灿';
      break;
    case 3:
      color = '绿油油';
      break;
    default:
      color = '五颜六色';
      break;
  }
```
等于
```python
  let condition = Math.ceil(Math.random()*5);
  let color = (condition==0 &&  '红艳艳') || (condition==1 &&  '黑乎乎') || (condition==2 &&  '黄灿灿') || (condition==3 &&  '绿油油') || '五颜六色';
```
等于
```python
  let condition = Math.ceil(Math.random()*5);
  let color = {'0': '红艳艳', '1': '黑乎乎', '2': '黄灿灿', '3': '绿油油'}[condition] || '五颜六色';
```
完美～～～


之后发现了再补～ ～ ～