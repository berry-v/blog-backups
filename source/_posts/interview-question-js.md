---
title: 问题-JavaScript
date: 2017-08-17 10:33:18
tags: [面试]
---

JavaScript相关

<!-- more -->

---

1. **算法和设计模式**
    >

1. **变量提升和函数提升 以及区别**
    >函数及变量的声明都将被解释器提升到函数的最顶部。
    变量可以在使用后声明，也就是变量可以先使用再声明。同一个变量只会声明一次，其他的会被忽略掉或者覆盖掉。
    函数声明式会提升到作用域最前边，并且将声明内容一起提升到最上边。

1. **宏任务，微任务**
    >宿主环境提供的叫宏任务，由语言标准提供的叫微任务
    
1. **promise和timeout异步的区别，执行的顺序**
    >Promise比setTimeout()先执行。
    因为Promise定义之后便会立即执行，其后的“.then()”不是正常的异步任务，而是微任务。
    而setTimeout()是异步的宏任务。
    宏任务追加到下一轮事件循环，微任务追加到本轮事件循环。这意味着，微任务的执行时间一定早宏任务。

1. **js事件流的过程**
    >
1. **防抖节流**
    >
1. **伪代码实现promise**
    >  
1. **浏览器本地存储（请描述一下 cookies, sessionstorage和 localstorage的区别）**
    >在HTML5中提供了sessionStorage和localStorage。
    sessionStorage用于本地存储一个会话（session）中的数据，这些数据只有在同一个会话中的页面才能访问并且当会话结束后数据也随之销毁，是会话级别的存储。
    localStorage用于持久化的本地存储，除非主动删除数据，否则数据是永远不会过期的。
1. **如何获取某个节点下的所有子节点**
    >
1. **循环一个数组有哪些方法?**
    > for、every、some、forEach、map、filter

1. **every、some、filter区别**
    > every() 测试一个数组内的所有元素是否都能通过某个指定函数的测试。返回Boolean。  
    filter() 方法创建一个新数组, 其包含通过所提供函数实现的测试的所有元素
    find() 方法返回数组中满足提供的测试函数的第一个元素的值。 
1. **for 循环优化（提高效率）**
    >  
1. **列举几个js中( 字符串 || 数组 || 对象)操作函数**
    >
1. **如果我要循环一个对象，用什么方法比较好。**
    >
1. **数组去重**
    >
1. **数字数组求和**
    >[10, 9, 8, 7, 6, 5, 4, 3, 2, 1].reduce((a, b) => a + b )

1. **二维数组，怎么变成一维数组**
    > [[1,2], ['a','b'], [{name:'张三'}], 'banabana'].flat()(flat 仅可扁平化二维数组，reduce，reduceRight)
1. **类型转换（例举几种强制类型转换和隐式类型转换）**
    > 强制: (通过方法转换)parseInt(), parseFloat(), Number(), String(), toString(), Boolean() 等
    隐式: ==, !!, >=, <=, !=, +, -, /, *, %, >, <, +=, -=, –, ++, &&, !, || 等
1. **js在什么时候会进行隐式类型转换，转换的结果？**
    >数值运算、if、调用方法或属性、!和!!
1. **js 如何判断网页中图片加载成功或者失败？**
    >onerror
    <element onerror="myScript">
    object.onerror=()=>{myScript};
1. **解释清楚 null 和 undefined**
    > null表示一个标识被赋值了，且该标识赋值为“空值”,从逻辑角度来看，null值表示空对象指针；
    undefined表示声明了标识，但没有给标识赋值。
1. **如何复制一个对象的值？（深拷贝、浅拷贝）**
    > 深浅拷贝
    Object.assign({}, obj) //只能深拷贝一层对象
    JSON.parse(JSON.stringify(obj)) //只在纯数据对象时使用
    遍历对象属性， 单个赋值
    var obj2 = {…obj1}

1. **减少页面加载时间的方法**
    > 尽量减少页面中重复的HTTP请求数量
    服务器开启gzip压缩
    css样式的定义放置在文件头部
    Javascript脚本放在文件末尾
    压缩合并Javascript、CSS代码
    使用多域名负载网页内的多个文件、图片
1. **谈谈This对象的理解**
    > 
1. **Javascript原型,原型链?有什么特点?**
    > 
1. **js中有哪些数据类型，并解释清楚原始数据类型和引用数据类型**
    > js中共有null,undefined, string,number,boolean,object六种数据类型。
    原始数据类型: null,undefined, string,number,boolean
    引用数据类型:object
    两者的区别：
    值存储方式不同：
    原始数据类型：将变量名和值都存储在栈内存中
    引用数据类型：将变量名存储在栈内存中，将值存储在堆内存中，并在栈内存中存储值的地址，该地址指向堆内存中的值。
1. **作用域与作用域链和闭包 闭包是什么,有什么特性,对页面有什么影响,简要介绍你理解的闭包**
    > 

1. **原型与原型连**
    > 

1. **谈谈你对前端性能优化的理解**
    >  
    a. 请求数量：合并脚本和样式表，CSS Sprites，拆分初始化负载，划分主域
    b. 请求带宽：开启GZip，精简JavaScript，移除重复脚本，图像优化，将icon做成字体
    c. 缓存利用：使用CDN，使用外部JavaScript和CSS，添加Expires头，减少DNS查找，配置ETag，使AjaX可缓存
    d. 页面结构：将样式表放在顶部，将脚本放在底部，尽早刷新文档的输出
    e. 代码校验：避免CSS表达式，避免重定向
1. **instanceof和typeof**
    > instanceof 运算符用来检测 constructor.prototype
    typeof 检查是什么类型的实例
1. **new操作符干了什么**
    > 创建一个空对象，并且 this 变量引用该对象，同时还继承了该函数的原型。
    属性和方法被加入到 this 引用的对象中。
    新创建的对象由 this 所引用，并且最后隐式的返回 this 。
1. **说一下自己常用的es6的功能？**
    >此题是一道开放题，可以自由回答。但要注意像let这种简单的用法就别说了，说一些经常用到并有一定高度的新功能
	像module、class、promise等，尽量讲的详细一点。
1. **谈谈BOM与DOM区别**
    > BOM浏览器对象模型
    DOM文档对象模型
1. **apply和call的作用和区别**
    > 作用：动态改变某个类的某个方法的运行环境（执行上下文）
    区别：传入参数形式不同
1. **创建ajax过程**
    > (1)创建XMLHttpRequest对象,也就是创建一个异步调用对象.
    (2)创建一个新的HTTP请求,并指定该HTTP请求的方法、URL及验证信息.
    (3)设置响应HTTP请求状态变化的函数.
    (4)发送HTTP请求.
    (5)获取异步调用返回的数据.
    (6)使用JavaScript和DOM实现局部刷新.
1. **正则表达式**
    > 
1. **匹配所有空格的正则表达式**
    > /\s*/g 
1. **你都使用哪些工具来测试代码的性能？**
    > JSPerf, Dromaeo
1. **demo**
    > 
    
# 代码
1. **函数对象方法**
    >函数对象的本身属性或方法的优先级要高于原型属性或方法

    ```javascript
        function fn () {
            this.a = 0
            this.b = function () {
                console.log(this.a)
            }
        }
        fn.prototype = {
            b: function () {
                this.a = 20
                console.log(this.a)
            },
            c: function () {
                this.a = 30
                console.log(this.a)
            }
        }
        var myfn = new fn()
        myfn.b() // 0
        myfn.c() // 30
        myfn.b() // 30
    ```

1. **变量提升和函数提升**
>引擎在读取js代码的过程中，分为两步。第一个步骤是整个js代码的解析读取，第二个步骤是执行。
在JS代码执行之前，浏览器的解析器在遇到 var 变量名 和function 整个函数 提升到当前作用域的最前面。
    >> 1.变量提升只会提升变量名的声明，而不会提升变量的赋值初始化。
    2.函数提升的优先级大于变量提升的优先级，即函数提升在变量提升之上。

    ```javascript
        var name = 'World!';
        (function () {
            // var name; // 3.变量提升在此隐式声明，所以name此时=undefined
            if (typeof name === 'undefined') { // 1.先在本函数作用域找变量
                // 4.由于name=undefined，所以这个判断条件成立
                var name = 'Jack' // 2.变量提升，隐式声明在函数开始时
                console.log('Goodbye ' + name) // 5.执行此语句
            } else {
                console.log('Hello ' + name)
            }
        })()
        // Goodbye Jack
    ```
    ```javascript
        console.log(a)
        var a = 1
        console.log(a)
        function a () { console.log(2) }
        console.log(a)
        var a = 3
        console.log(a)
        function a () { console.log(3) }
        a()
        console.log(a)

        // ƒ a(){ console.log(3) } // var a提升,但变量名与函数名相同，故function a()提升时将覆盖var a,又因同名的function函数，后写的将覆盖先写的，所以最后提升的只有function a(){ console.log(3) }
        // 1
        // 1
        // 3
        // Uncaught TypeError: a is not a function // 此时a为一个变量，不再是一个函数，所以报错，js中一旦出现报错，后面的语句将不再运行，所以最后一个console.log不进行打印。
    ```

1. **原型 原型链 new操作符**
    ```javascript
        function A () {
            a = function () { console.log(1) }
        }
        A.a = function () { console.log(2) }
        A.prototype.a = function () { console.log(3) }
        var a = function () { console.log(4) }
        function a () { console.log(5) }

        a() // 4
        A() // 无
        A.a() // 2
        a() // 1
        new A.a() // 2  // 直接new的A.a() 执行了A.a 的内容
        new A().a() // 3 // new的A()产生了一个实例， 再调用了实例上的a方法
    ```

1. **settimeout与promise执行顺序**
    >Promise比setTimeout()先执行。
    因为Promise定义之后便会立即执行，其后的.then()是异步里面的微任务。
    而setTimeout()是异步的宏任务。

    ```javascript
        setTimeout(function () { console.log(4) }, 0)
        new Promise(function (resolve) {
            console.log(1)
            for (var i = 0; i < 10000; i++) {
                i === 9999 && resolve()
            }
            console.log(2)
        }).then(function () {
            console.log(5)
        })
        console.log(3)

        // 1
        // 2
        // 3
        // 5
        // 4
    ```

1. **js实现类似于add(1)(2)(3)调用方式的方法**
    >实现函数f
    f(1) = 1
    f(1)(2) = 3
    f(1)(2)...(n) = 1+2+...+n

    ```javascript
        function f (x) {
            var sum = x
            var tmp = function (y) {
                sum = sum + y
                return tmp
            }
            tmp.toString = function () {
                return sum
            }
            return tmp
        }
        console.log(f(1)(2)(3)) // 6
        console.log(f(1)(2)(3)(4)) // 10
        // 首先要一个数记住每次的计算值，所以使用了闭包，在tmp中记住了x的值，第一次调用f(),初始化了tmp，并将x保存在tmp的作用链中，然后返回tmp保证了第二次调用的是tmp函数，后面的计算都是在调用tmp, 因为tmp也是返回的自己，保证了第二次之后的调用也是调用tmp，而在tmp中将传入的参数与保存在作用链中x相加并付给sum，这样就保证了计算
        // 但是在计算完成后还是返回了tmp这个函数，这样就获取不到计算的结果了，我们需要的结果是一个计算的数字，首先要知道JavaScript中，打印和相加计算，会分别调用toString或valueOf函数，所以我们重写tmp的toString和valueOf方法，返回sum的值
    ```

    ```javascript
        function f(x) {
            var result = (y) => f(x+y)
            result.toString = () => x
            return result
        }
    ```

---