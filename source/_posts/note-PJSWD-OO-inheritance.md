---
title: JavaScript 面向对象之继承
date: 2018-04-17 14:07:24
tags: [JavaScript, 面向对象]
---

阅读 Professional JavaScript for Web Developers 笔记之面向对象的继承

<!-- more -->
## 一、原型链
原型链基本思想是利用原型让一个引用类型继承另一个引用类型的属性和方法。
构造函数、原型、实例之间的关系： 每个构造函数都有一个原型对象， 原型对象都包含一个指向构造函数的指针， 而实例都包含一个指向原型对象的内部指针。
```javascript
function SuperType(){
  this.property = true;
}
SuperType.prototype.getSuperValue = function(){
  return this.property;
}

function SubType(){
  this.subproperty = false;
}
SubType.prototype = new SuperType();
SubType.prototype.getSubValue = function(){
  return this.subproperty;
}

var instance = new SubType();
```
弊端： 如果原型中包含引用类型（例如Array）, 那么在通过原型来实现继承时，原型对象中的实例属性在被继承后变成了现在的原型属性。由于包含引用类型值的原型属性会被所有实例共享，那么引用类型（例如Array）也会被实例共享。就会出现一个实例中修改了属性， 另一个实例中访问属性就变成了修改后的的情况。
```javascript
function SuperType(){
  this.colors = ['red', 'blue', 'green'];
}

function SubType(){}
SubType.prototype = new SuperType();

var instance1 = new SubType();
instance1.colors.push('black');
console.log(instance1.colors); //["red", "blue", "green", "black"]

var instance2 = new SubType();
console.log(instance2.colors); //["red", "blue", "green", "black"]
```

## 二、借用构造函数（利用call() 和 apply()）
为解决原型中包含引用类型所带来的问题
思想： 在子类构造函数的内部调用超类型的构造函数
如下例， 实际上是在新创建的SubType实例环境下调用了SuperType构造函数， 这样就会在新的SubType对象上执行SuperType()函数中定义的所有对象初始化代码。
```javascript
function SuperType(){
  this.colors = ['red', 'blue', 'green'];
}

function SubType(){
  SuperType.call(this);
}

var instance1 = new SubType();
instance1.colors.push('black');
console.log(instance1.colors); //["red", "blue", "green", "black"]

var instance2 = new SubType();
console.log(instance2.colors); //["red", "blue", "green"]
```

## 三、 组合式继承 （伪经典继承） （最常用）
将原型链和借用构造函数组合到一起， 集两者之长
```javascript

function SuperType(name){
  this.name = name;
  this.colors = ['red', 'blue', 'green'];
}
SuperType.prototype.sayName = function(){
  console.log(this.name);
}

function SubType(name, age){
  SuperType.call(this, name);
  this.age = age;
}
SubType.prototype = new SuperType();
SubType.prototype.constructor = SubType;
SubType.prototype.sayAge = function(){
  console.log(this.age);
}

var instance1 = new SubType('菠萝吹雪', 18);
instance1.colors.push('black');
console.log(instance1.colors); //["red", "blue", "green", "black"]
instance1.sayName(); //菠萝吹雪
instance1.sayAge(); //18

var instance2 = new SubType('橙留香', 18);
console.log(instance2.colors); //["red", "blue", "green"]
instance2.sayName(); //橙留香
instance2.sayAge(); //18
```

## 四、原型式继承
借助于原型可以给予已有的对象创建新对象， 同时还不必因此创建自定义类型
可用Object.create()方法来实现
```javascript
var person = {
  name: '菠萝吹雪',
  friends: ['橙留香', '陆小果', '菠萝小薇']
}
var person1 = Object.create(person);
person1.name = '橙留香';
person1.friends.push('梨花诗');
console.log(person1.friends); //["橙留香", "陆小果", "菠萝小薇", "梨花诗"]

var person2 = Object.create(person);
person2.name = '陆小果';
person2.friends.push('上官子怡');
console.log(person2.friends); //["橙留香", "陆小果", "菠萝小薇", "梨花诗", "上官子怡"]
```


## 五、 extends
用class关键字来定义的类， 需要用extends来继承， 在类声明或表达式中创建一个类作为另一个类的子类
可以再constructor中调用super调用超类

```javascript
class Animal{
  constructor(name){
    this.name = name;
  }
  speak(){
    console.log(`${this.name} 在说话`);
  }
}
class Dog extends Animal{
  constructor(name, leg){
    super(name);
    this.legNum = leg;
  }
  leg(){
    console.log(`${this.name} 有 ${this.legNum}条腿`);
  }
}

let corgi = new Dog('柯基', 4);
```
