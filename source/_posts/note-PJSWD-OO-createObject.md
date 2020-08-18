---
title: JavaScript 面向对象之创建对象
date: 2018-04-16 16:52:18
tags: [JavaScript, 面向对象]
---

阅读 Professional JavaScript for Web Developers 所做的笔记
最近一直在阅读JavaScript高级程序设计（第三版）
正好， 现在阅读到比较重要的面向对象的程序设计， 对此做一个阅读笔记， 一是为了加深印想， 二是为了抓一个重点
<!-- more -->

## 一、工厂模式
ES中无法创建类， 所以创建一个函数来封装以特定接口创建对象的细节
缺点： 无法知道一个对象的类型
```javascript
function person(name, age, job){
  let o = new Object();
  o.name = name;
  o.age = age;
  o.job = job;
  return o;
}
let person1 = person('菠萝吹雪', 18, '剑客');
```

## 二、构造函数模式
ES中构造函数可以用来创建特定类型的对象
构造函数的函数名始终都应该以一个大写字母开头， 非构造函数则应该以一个小写字母开头。
需要使用new操作符来创建一个实例。实际上会经历一下四个步骤：
1) 创建一个新对象；
2) 将构造函数中的作用域赋给新对象(因此this就指向了这个新对象)；
3) 执行构造函数中的代码(为这个新对象添加属性)；
4) 返回新对象；
任何函数只要通过new操作符来调用， 那他就可以作为构造函数；
而任何函数， 如果不通过new操作符来调用， 那他跟普通函数也不会有什么两样；
创建自定义的构造函数意味着将来可以将他的实例标识为一种特定的类型；（如下例子中， person1是Person类型的）
缺点： ES中每个函数是对象， 因此每定义一个函数就是实例化了一个对象， 所以函数中的每个方法都要在每个实例上重新创建一遍（如下例子中的sayName()）
```javascript
function Person(name, age, job){
  this.name = name;
  this.age = age;
  this.job = job;
  this.sayName = function(){
    console.log(this.name);
  }
}
let person1 = new Person('橙留香', 18, '剑客');
```

## 三、原型模式
每个函数都有一个原型属性（prototype）， 这个属性是一个指针， 指向一个对象。就是通过调用构造函数而创建的那个实例对象的原型对象。
```javascript
function Person(){}
Person.prototype.name = '陆小果';
Person.prototype.age = 18;
Person.prototype.job = '剑客';
Person.prototype.sayName = function(){
  console.log(this.name);
};

let person1 = new Person();
```
更简单的原型语法
把原型模式简写了， 但简写了之后相当于重写了所有的prototype， 所以不会自动创建constructor， 所以如果constructor很重要的话就必须将constructor设置回适当的值，但是这样会导致constructor的[[enumerable]] 被设置为true， 默认情况下， 原生的constructor属性是不可以枚举的， 所以也可以使用Object.defineproperty()来改变
```javascript
function Person(){}
Person.prototype = {
  name:'陆小果',
  age: 18,
  job: '剑客',
  sayName: function(){
    console.log(this.name);
  }
}
Object.defineProperty(Person.prototype, 'constructor', {
  enumerable: false,
  valye: Person
});

let person = new Person();
console.log(person);
```

## 四、组合使用构造函数模式和原型模式（最常见）
构造函数模式用于定义实力属性， 原型模式用于定义方法和共享属性。集两种模式之长。
```javascript
function Person(name, age, job){
  this.name = name;
  this.age = age;
  this.jpb = job;
}
Person.prototype = {
  constructor: Person,
  sayName: function(){
    console.log(this.name);
  }
}
let person1 = new Person('菠萝小薇', 18, '剑客');
```

## 五、动态原型模式
把所有的信息都封装在了构造函数中， 而通过构造函数中初始化原型， 又保持了同时使用构造函数和原型的优点。即通过检查某个应该存在的方法是否有效来决定是否需要初始化原型。
如下例中， 只需要判断任何一个原型中应该存在的属性或方法， 不必检查每个属性和方法。
```javascript
function Person(name, age, job){
  this.name = name;
  this.age = age;
  this.job = job;
  if(typeof this.sayName != "function"){
    Person.prototype.sayName = function(){
      console.log(this.name);
    }
    Person.prototype.sayAge = function(){
      console.log(this.age);
    }
  }
}
let person1 = new Person('梨花诗', 18, '剑客');
```

## 六、寄生构造函数模式
不推荐， 除非有特殊需要
## 七、稳妥构造函数模式
不推荐， 除非有特殊需要

## 八、ES6 Class
ES6 引入了类（class）的概念， 可以通过class关键字来定义类。
这个类的存在， 多被认为是一个ES5的 组合使用构造函数模式和原型模式 的一个语法糖， 示例如下
但class定义的类中的方法的enumerable属性是false, 都是不能被枚举的。
用static关键字可以定义一个类的一个静态方法， 调用静态方法不需要实例化该类， 但不能通过一个类实例调用静态方法。通常静态方法用于为一个应用程序创建工具函数
```javascript
class Person{
  constructor(name, age, job){
    this.name = name;
    this.age = age;
    this.job = job;
  }
  sayName(){
    console.log(this.name);
    Person.logAge(this.age);
  }
  static logAge(age){
    console.log(age);
  }
}
let person1 = new Person('风清扬方丈', 92, '武术师傅');
```
