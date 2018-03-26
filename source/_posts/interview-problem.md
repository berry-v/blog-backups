---
title: 记所遇面试题
date: 2018-03-23 11:23:34
tags: [JavaScript, 面试题]
---

面试已经过去有几天， 对其中某几个问题表示很是好奇， 虽然工作中很少或者没有遇到过此类问题， 但答案还是要给自己的， 以上。
<!-- more -->
## 一、使（a==1 && a==2 && a==3）结果为true
当最开始看到这个问题的时候， 内心OS： 这TM怎么可能。 然而真的是可能的， 且方法还不少， 呵呵哒， 为自己的无知沉默三分钟。 下面继续答案：
### 1)、defineProperty
```python
var val = 0;
Object.defineProperty(window, 'a', {
  get: function(){
    return ++val;
  }
});
if( a==1 && a==2 && a==3){
  console.log('就说是可能的吧～～～');
}
```
### 2)、defineProperties
```python
var val = 0;
Object.defineProperties(window, {
  'a':{
    get: function(){
      return ++val;
    }
  }
});
if( a==1 && a==2 && a==3){
  console.log('你还不相信～～～');
}
```
### 3)、valueOf
```python
var a = {
  val: 0,
  valueOf: function(){
    return ++this.val;
  }
}
if( a==1 && a==2 && a==3){
  console.log('这下打脸了吧～～～');
}
```
### 4)、toString
```python
var a = {
  val: 1,
  toString: function(){
    return this.val++;
  }
}
if( a==1 && a==2 && a==3){
  console.log('疼不疼～～～');
}
```

## 二、有数组[1, 2, 3, 4, 5, 6, 7, 6, 5, 4, 3, 2, 1]， 最快的去重方法
其实说起来真没关注过这些个问题， 当时就想到了Set可以去重， 写法也挺简单， 但后来发现不一定是最快的

### 1)、Set
```python
console.time();
const arr = [1, 2, 3, 4, 5, 6, 7, 6, 5, 4, 3, 2, 1];
console.log([...new Set(arr)]);
console.timeEnd();
```
### 2)、循环判断
```python
console.time();
const arr = [1, 2, 3, 4, 5, 6, 7, 6, 5, 4, 3, 2, 1]
const res = []
for(let i = 0; i < arr.length; res.indexOf(arr[i++]) === -1 && res.push(arr[i - 1]));
console.log(res);
console.timeEnd();
```
## 三、JS对象的深拷贝
### 1)、Object.assign //只能深拷贝一层对象
```python
Object.assign({}, obj)
```
### 2)、JSON  //只在纯数据对象时使用
```python
JSON.parse(JSON.stringify(obj));
```
### 3)、遍历对象属性， 单个赋值
```python
for(var key in obj1){
  obj2[key] = obj1[key]
}
```
### 4)、...
```python
var obj2 = {...obj1};
```

## 四、输出结果
函数对象的本身属性或方法的优先级要高于原型属性或方法
其实是一道很简单的题， 答错真的很不应该
```python
function fn(){
  this.a = 0;
  this.b = function(){
    console.log(this.a);
  }
}
fn.prototype = {
  b: function(){
    this.a = 20;
    console.log(this.a);
  },
  c: function(){
    this.a = 30;
    console.log(this.a);
  }
}
var myfn = new fn();
myfn.b(); //0
myfn.c(); //30
myfn.b(); //30
```

## 五、输出结果
变量名提升
```python
var name = 'World!';
(function(){
  if(typeof name === 'undefined'){
    var name = 'Jack';
    console.log('Goodbye ' + name);
  } else {
    console.log('Hello ' + name);
  }
})();
//Goodbye Jack
```
