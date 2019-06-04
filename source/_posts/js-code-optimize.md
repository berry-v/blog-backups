---
title: js 中可优化的代码片段
date: 2019-05-04 10:03:42
tags: [js, 优化]
---

你有没有见过这样的代码

```javascript
if (type !== 'default') {
    slot = {
        type: 'text',
        value: 'gulugulugulu~~~~'
    }
} else {
    slot = {
        type: 'text',
        value: ''
    }
}

```

<!-- more -->

这样的代码

```javascript
if (nodeList[i].className === 'topLeft') {
} else if (nodeList[i].className === 'topCenter') {
} else if (nodeList[i].className === 'topRight') {
} else if (nodeList[i].className === 'bottomRight') {
} else if (nodeList[i].className === 'bottomCenter') {
} else if (nodeList[i].className === 'bottomLeft') {
} else if (nodeList[i].className === 'middleLeft') {
} else if (nodeList[i].className === 'middleRight') {
} else {
}

```

这样的代码

```javascript
if ( param === 1 || param === 2 || param === 3 || param === 'a' || param === 'b' ) {}

```

我们在编写 js 代码的时候， 可能在很多时候就是写出来的代码， 实现了他的功能然后测一下没问题之后就没有然后了， 但是有时候我们是可以对代码本身做一些优化的，这可能是很小的一些问题， 但是也是很容易被忽略的一些问题。
比如时常会遇到一些比如判断啊或者其他的什么的， 在语句逐渐变得多了之后， 代码没处理好可能就会比较臃肿， 然后一时又想不到该怎么去优化，在此提供一些可参考的代码示例

# 条件判断

## if-else

多数的嵌套判断， 都是可以被简化的

```javascript
if (!isEdit) {
    return false
} else {
    if (type === 'stars') {
        return true
    } else {
        return false
    }
}

//---------------------------

return isEdit && type === 'stars'

```

用三元运算符代替简单的, 虽然这个大家都知道， 但是代码中还是很多这种代码， 可以稍微注意一下

```javascript
if (attributes.slot !== 'default') {
    attributes.slot = {
        type: 'text',
        value: attributes.slot
    }
} else {
    attributes.slot = {
        type: 'text',
        value: ''
    }
}

//---------------------------
attributes.slot = {
    type: 'text',
    value: attributes.slot === 'default' ? '' : attributes.slot
}

```

## 多个 if... else if...

我们在写 js 的时候时长会遇到复杂逻辑判断的情况， 通常大家都会用 if ... else if 或者 switch 来实现多个条件的判断， 但是这时就有一个问题， 随着条件越来越多，代码中的 if else/switch 会越来越臃肿， 虽然不会说看不懂， 但是在某些情况下看着就没有那么直观， 比如以下这种

```javascript
if (nodeList[i].className === 'topLeft') {
    nodeList[i].onmousedown = e => {
        _this.onDragDown(e, 'nw')
    }
} else if (nodeList[i].className === 'topCenter') {
    nodeList[i].onmousedown = e => {
        _this.onDragDown(e, 'n')
    }
} else if (nodeList[i].className === 'topRight') {
    nodeList[i].onmousedown = e => {
        _this.onDragDown(e, 'ne')
    }
} else if (nodeList[i].className === 'bottomRight') {
    nodeList[i].onmousedown = e => {
        _this.onDragDown(e, 'ne')
    }
} else if (nodeList[i].className === 'bottomCenter') {
    nodeList[i].onmousedown = e => {
        _this.onDragDown(e, 's')
    }
} else if (nodeList[i].className === 'bottomLeft') {
    nodeList[i].onmousedown = e => {
        _this.onDragDown(e, 'sw')
    }
} else if (nodeList[i].className === 'middleLeft') {
    nodeList[i].onmousedown = e => {
        _this.onDragDown(e, 'w')
    }
} else if (nodeList[i].className === 'middleRight') {
    nodeList[i].onmousedown = e => {
        _this.onDragDown(e, 'e')
    }
} else {
    nodeList[i].onmousedown = e => {
        _this.onDragDown(e, 'default')
    }
}

```

在上边这段代码中， 很多 else if, 根据不同的 class 名称， 传不同参数调用同一个方法
改成 switch, 看起来并没有好很多

```javascript
switch (nodeList[i].className) {
    case 'topLeft':
        nodeList[i].onmousedown = e => {
            _this.onDragDown(e, 'nw')
        }
        break
    case 'topCenter':
        nodeList[i].onmousedown = e => {
            _this.onDragDown(e, 'n')
        }
        break
    case 'topRight':
        nodeList[i].onmousedown = e => {
            _this.onDragDown(e, 'ne')
        }
        break
    case 'bottomRight':
        nodeList[i].onmousedown = e => {
            _this.onDragDown(e, 'ne')
        }
        break
    case 'bottomCenter':
        nodeList[i].onmousedown = e => {
            _this.onDragDown(e, 's')
        }
        break
    case 'bottomLeft':
        nodeList[i].onmousedown = e => {
            _this.onDragDown(e, 'sw')
        }
        break
    case 'middleLeft':
        nodeList[i].onmousedown = e => {
            _this.onDragDown(e, 'w')
        }
        break
    case 'middleRight':
        nodeList[i].onmousedown = e => {
            _this.onDragDown(e, 'e')
        }
        break
    default:
        nodeList[i].onmousedown = e => {
            _this.onDragDown(e, 'default')
        }
}

```

利用 Object
将判断条件作为对象的属性名，将处理逻辑作为对象的属性值，在按钮点击的时候，通过对象属性查找的方式来进行逻辑判断。

```javascript
const classNames = {
    topLeft: 'nw',
    topCenter: 'n',
    topRight: 'ne',
    bottomRight: 'ne',
    bottomCenter: 's',
    bottomLeft: 'sw',
    middleLeft: 'w',
    middleRight: 's'
}
nodeList[i].onmousedown = e => {
    _this.onDragDown(e, classNames[nodeList[i].className] || 'default')
}

```

用 Map

```javascript
const classNames = new Map([
    ['topLeft', 'nw'],
    ['topCenter', 'n'],
    ['topRight', 'ne'],
    ['bottomRight', 'ne'],
    ['bottomCenter', 's'],
    ['bottomLeft', 'sw'],
    ['middleLeft', 'w'],
    ['middleRight', 's']
])
nodeList[i].onmousedown = e =>
    _this.onDragDown(e, classNames.get('middleLeft') || 'default')

```

用 Map 对象和 Object 对象有什么区别呢?
一个对象通常都有自己的原型，所以一个对象总有一个"prototype"键。
一个对象的键只能是字符串或者 Symbols，但一个 Map 的键可以是任意值。
在我看来， 用 Map 和 Object 无论哪个都好， 至少看起来比 if 和 switch 好

## 一个 if 中的多个条件判断

感觉这个也是一个比较常出现的一个情况， 在一个条件判断语句中， 有多重条件可以通过次验证的情况
可以利用数组来和数组自带的方法来处理这种情况

```javascript
if ( param === 1 || param === 2 || param === 3 || param === 'a' || param === 'b') {}

// -------------------------------

if ([1, 2, 3, 'a', 'b', 'c'].includes(param)) {}

```

```javascript
if ( param !== 1 && param !== 2 && param !== 3 && param !== 'a' && param !== 'b') {}

// -------------------------------

if (![1, 2, 3, 'a', 'b', 'c'].includes(param)) {}

```

# 利用数据和符号， 在可读范围内

在可读范围内使用运算符来简化代码的逻辑
比如 !除了做逻辑运算之外还可以用于取得一个布尔值， 举个例子， 在我们现在是用的 iview 的源码中， 就很多关于!!的使用， 原理就是!!可以把数据转换为布尔类型， 然后用于判断

```javascript
if (value === '' || value === 0 || value === null || value === undefined) { }

// -----------------------

if (!value) { }

```

```javascript
// 这是iview里的代码片段
classes () {
    return [
        `${prefixCls}`,
        `${prefixCls}-${this.shape}`,
        `${prefixCls}-${this.size}`,
        {
            [`${prefixCls}-image`]: !!this.src,
            [`${prefixCls}-icon`]: !!this.icon || !!this.customIcon
        }
    ];
},

```

&&

```javascript
type === 'drag' && dragOver()

```

当然， 其他符号也有自己不同的作用， 也可以根据情况使用， 但是一定要保持在可读范围内
比如 (n&1 ? '奇数' : '偶数') 可以用来判断基数和偶数，
原理是在使用按位与（&）运算时 二进制位数对比都为 1 时才为 1
十进制转换为二进制后， 末位数为 1 即奇数， 末位数为 0 即偶数

同样的按位或（|）运算时 由于浮点数不支持位运算， 所以自动转换为整数， 再进行运算。
因为这个特性， 可以取巧， 用来做向下运算。
所以（1.23|0）结果是为 1

<b>但是以上两种可读性不是很高， 所以不建议使用</b>

# 避免使用 for...in

遍历对象的时候尽可能少的使用 for...in, 因为 for in 会遍历原型上所能枚举的属性，可以用 Object.keys()来遍历

```javascript
Object.keys(objParam).forEach(key => {
    console.log(objParam[key])
})

```

# 尽可能的使用内置方法

在 js 的内置对象中现在已经提供了很多内置方法并且还有各种高阶函数
平时在操作这些内置对象的时候， 如果内置方法可以满足需要的时候， 尽量使用内置方法(大多数时候， 内置方法都可以满足需要)

以数组为例
数组对象
比如如下数组去重（虽然有更简单的 Set 可以用于去重）

```javascript
const arr1 = [1, 2, 1, 2, 3, 5, 4, 5, 3, 4, 4, 4, 4]
const arr2 = []
for (let i = 0; i < arr1.length; i++) {
    if (arr1.indexOf(arr1[i]) === i) {
        arr2.push(arr1[i])
    }
}

// ---------------------------
const arr1 = [1, 2, 1, 2, 3, 5, 4, 5, 3, 4, 4, 4, 4]
const arr2 = arr1.filter( (element, index, self) => self.indexOf(element) === index )
// arr2  [1, 2, 3, 5, 4]
// arr1  [1, 2, 1, 2, 3, 5, 4, 5, 3, 4, 4, 4, 4]

```

现在有一个数组 [0, 1, 2, 3, 4]，需要计算数组元素的和

```javascript
const arr = [0, 1, 2, 3, 4]
let sum = 0
for (let i = 0; i < arr.length; i++) {
    sum += arr[i]
}

//------------------------- 

const arr = [0, 1, 2, 3, 4]
let sum = arr.reduce((accumulator, currentValue) => accumulator + currentValue)

```

拷贝数组

```javascript
let arr = [1, 2, 3, 4, 5]
let arrCopy = arr.slice()

```

# 思考题

使（a==1 && a==2 && a==3）结果为 true
