---
title: js 中可优化的代码片段
date: 2019-06-03 10:03:42
tags: [js, 优化]
---

我们在编写 js 代码的时候， 时常会遇到一些比如判断啊什么的， 在语句逐渐变得多了之后， 代码没处理好可能就会比较臃肿， 然后一时又想不到该怎么去优化，在此提供一些可参考的代码示例

<!-- more -->

# 条件判断

## if-else

用三元运算符代替简单的, 虽然这个大家都知道， 但是代码中还是很多这种代码， 可以稍微注意一下

```javascript
// 比如
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

// 可以改成
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
nodeList[i].onmousedown = e =>
    _this.onDragDown(e, classNames[nodeList[i].className] || 'default')
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

感觉这个也是一个比较常出现的一个情况

```javascript
// 比如
if (
    param === 1 ||
    param === 2 ||
    param === 3 ||
    param === 'a' ||
    param === 'b'
) {
}
// 可以改成
if ([1, 2, 3, 'a', 'b', 'c'].includes(param)) {
}
```

# if 与 array

# 尽可能的使用内置方法

在 js 的内置对象中现在已经提供了很多高阶函数

#对象的操作

##避免使用 for...in
遍历对象的时候尽可能少的使用 for...in, 因为 for in 会遍历原型上所能枚举的属性，可以用 Object.keys()来遍历

```javascript
Object.keys(objParam).forEach(key => {
    console.log(objParam[key])
})
```

# 数组

## 拷贝数组

```javascript
let arr = [1, 2, 3, 4, 5]
let arrCopy = arr.slice()
```

# 思考题

使（a==1 && a==2 && a==3）结果为 true
