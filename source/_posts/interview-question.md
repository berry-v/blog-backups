---
title: 面试题
date: 2017-02-18 11:46:53
tags: [面试]
---

可能遇到的面试题总结

<!-- more -->

# HTML

---

1.  **简述一下你对 HTML 语义化的理解，知道的语义化标签**

    > 直观的认识标签对于搜索引擎的抓取有好处，用正确的标签做正确的事情！
    > HTML 语义化就是让页面的内容结构化，便于对浏览器，搜索引擎解析;
    > 在没有样式 css 情况下也以一种文档格式显示，并且是容易阅读。搜索引擎的爬虫依赖于标记来确定上下文和各个关键字的权重，利于 SEO。
    > 在阅读源代码的人对网站更容易将网站分块，便于阅读维护理解。

1.  **html5 有哪些新特性**

    > HTML5 现在已经不是 SGML 的子集，主要是关于图像，位置，存储，多任务等功能的增加
    > 绘画 canvas
    > 用于媒介回放的 video 和 auto 元素;
    > 本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失;
    > sessionStorage 的数据在浏览器关闭后自动删除;
    > 语意化更好的内容元素，比如 article、footer、header、nav、section;
    > 表单控件：calendar、date、time、url、search;

1.  **html5 哪些操作可以 SEO 优化**

    > title 标签;meta 标签;header 标签;footer 标签;元标签（meta 标签）;导航标签（nav 标签）;文章标签（article 标签）;左或右侧标签（aside 标签）

1.  **默认情况下，使用 h1 标签会形成什么效果?**

    > 加粗、大号文字

1.  **列举几个行内元素和块级元素, 说说他们的特性**

    > 块级元素：默认宽度 100%(占满一行),垂直方向排列,自动换行,可以使用 CSS 设置宽度高度
    > 常用的块级元素有 div、 p、 h1-h6、ol、ul、dl、table、address、blockquote、form
    > 内联元素：默认宽度由内容撑开(内容多宽、宽度就占多宽),水平方向排列,width 无效,height 无效,margin 上下无效，padding 上下无效
    > 常用的内联元素有:a、span、br、i、em、strong、label、q、var、cite
    > 常用的行内块元素有：img、input

1.  **在新窗口打开链接的方法是？**

    > target:\_blank

    ```html
    <a target="_blank" href="#"></a>
    ```

---

---

# CSS

---

1. **CSS 的盒子模型**

    > border，margin,padding
    > box-sizing 属性
    > content-box:这是默认样式指定 CSS 标准。测量 width 和 height 属性只包括的内容，但不是 border, margin, 或者 padding。
    > border-box:widt eight 属性包括 padding 和 border，但不是 margin。这是盒模型的文档时，Internet Explorer 使用 Quirks 模式。
    > padding-box:wid height 属性包括 padding 的大小，不包括 border 和 margin

1. **盒子水平垂直居中**

    ```html
    <div class="content">
        <div class="center">Center</div>
    </div>
    ```

    > display:flex

    ```css
    .content {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100%;
    }
    .center {
        border: 1px solid #999;
    }
    ```

    > position: absolute(同 position:absolute 一样， position:relative 也同样可以使元素居中， 且有多种方法。思路基本同 position:absolute 一样)

    ```css
    .content {
        position: relative;
        height: 100%;
    }
    .center {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        border: 1px solid #999;
    }
    /* 或者 */
    .content {
        position: relative;
        height: 100%;
    }
    .center {
        position: absolute;
        top: 50%;
        left: 50%;
        margin: -50px auto auto -50px;
        border: 1px solid #999;
        width: 100px;
        height: 100px;
    }
    /*再或者*/
    .content {
        position: relative;
        height: 100%;
    }
    .center {
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

1. **css3 新特性**

    > 颜色：新增 RGBA、HSLA 模式
    > 文字阴影(text-shadow)
    > 边框：圆角（border-radius）边框阴影：box-shadow
    > 盒子模型：box-sizing
    > 背景：background-size 设置背景图片的尺寸，background-origin 设置背景图片的原点，background-clip 设置背景图片的裁剪区域，以“，”分隔可以设置多背景，用于自适应布局
    > 渐变：linear-gradient、radial-gradient
    > 过渡：transition 可实现动画
    > 自定义动画
    > 在 CSS3 中唯一引入的伪元素是::selection
    > 多媒体查询、多栏布局
    > border-image
    > 2D 转换：transform:translate(x,y)rotate(x,y)skew(x,y)scale(x,y)
    > 3D 转换

1. **如何实现半透明边框、圆角边框、怎么添加阴影**
    >
1. **谈谈 css3 动画 transform、animation 和 transition**
    >
1. **用过哪些 CSS 预处理器，介绍下它们的特性（Less、Sass、Stylus）**
    >
1. **CSS 清除浮动的几种方法**

    > 使用带 clear 属性的空标签
    > 使用 css 的 overflow 属性
    > 使用 css 的伪元素:after 和 zoom(zoom 是为了兼容 IE6，7)
    > 以浮制浮（父级同时浮动）
    > 给父元素添加 overflow：hidden 清除浮动方法;
    > 父级设置成 inline-block;
    > 结尾处加 br 标签 clear:both。

1. **CSS 隐藏元素的几种方法**

    > display:none
    > visiblity:hidden
    > height:0
    > opacity: 0

1. **css 选择器优先级是怎样的**

    > !important>行内样式>id 选择器>类选择器>标签选择器>通配符>继承

1. **列举几个可以继承的和不可继承的 css 属性**

    > 可继承的属性：font-size, font-family, color
    > 不可继承的样式：border, padding, margin, width, height

1. **box-sizing、transition、translate 分别是什么？**

    > box-sizing:用来指定模型的大小的计算方式。主要分为 border-box(从边框固定盒子大小)、content-box(从内容固定盒子大小)两种计算方式。
    > transition:当前元素只要有"属性"发生变化时，可以平滑的进行过渡。通过 transition-propety 设置过渡属性;transition-duration 设置过渡时间;transition-timing-function 设置过渡速度;transition-delay 设置过渡延时。
    > translate：通过移动改变元素的位置;有 x,y,z 三个属性

1. **display 有哪些值？说明它们的作用。**

    > block 块类型。默认宽度为父元素宽度，可设置宽高，换行显示。
    > none 缺省值。像行内元素类型一样显示。
    > inline 行内元素类型。默认宽度为内容宽度，不可设置宽高，同行显示。
    > inline-block 默认宽度为内容宽度，可以设置宽高，同行显示。
    > list-item 像块类型元素一样显示，并添加样式列表标记。
    > table 此元素会作为块级表格来显示。
    > inherit 规定应该从父元素继承 display 属性的值。

1. **px、em、rem 的区别**

    >

1. **什么是响应式设计？响应式设计的基本原理是什么？**

    > 响应式网站设计是一个网站能够兼容多个终端，而不是为每一个终端做一个特定的版本。
    > 基本原理是通过媒体查询检测不同的设备屏幕尺寸做处理。

1. **弹性布局 flex**

    >

1. **CSS 优化、提高性能的方法有哪些**

    > 避免过度约束
    > 避免后代选择符
    > 避免链式选择符
    > 使用紧凑的语法
    > 避免不必要的命名空间
    > 避免不必要的重复
    > 最好使用表示语义的名字。一个好的类名应该是描述他是什么而不是像什么
    > 避免！important，可以选择其他选择器
    > 尽可能的精简规则，你可以合并不同类里的重复规则

1. **怎么让 Chrome 支持小于 12px 的文字？**
    > 使用 transform 缩放 transform:scale(0.8)

---

---

# JS

---

1. **谈谈 BOM 与 DOM 区别**

    >

1. **JavaScript 有哪些数据类型？**

    > 对变量的作用域的理解
    > 原生对象，原生对象的具体方法
    > 列举几个 js 中字符串操作函数

1. **循环一个数组有哪些方法?for 循环优化（提高效率）？every、some、forEach、map、filter 区别**

    >

1. **html5 离线存储有哪些, 请描述一下 cookies, sessionstorage 和 localstorage 的区别**

    >

1. **instanceof 和 typeof**

    >

1. **new 操作符具体干了什么**

    >

1. **作用域与作用域链和闭包**

    >

1. **闭包是什么,有什么特性,对页面有什么影响,简要介绍你理解的闭包**

    >

1. **原型与原型连**

    > 谈谈 This 对象的理解

1. **创建 ajax 过程, ajax 请求的时候 get 和 post 方式的区别**

    >

1. **es6、用过哪些**

    >

1. **apply 和 call 的作用和区别**

    >

1. **类型转换（例举几种强制类型转换和隐式类型转换）**

    > 强制: (通过方法转换)parseInt(), parseFloat(), Number(), String(), toString(), Boolean() 等
    > 隐式: ==, !!, >=, <=, !=, +, -, /, \*, %, >, <, +=, -=, --, ++, &&, !, || 等

1. **列举常用的操作数组的方法**

    > 数组方法 pop push unshift shift

1. **深浅拷贝**

    > Object.assign({}, obj) //只能深拷贝一层对象
    > JSON.parse(JSON.stringify(obj)) //只在纯数据对象时使用
    > 遍历对象属性， 单个赋值
    > var obj2 = {...obj1}

1. **事件冒泡**

    >

1. **js 如何判断网页中图片加载成功或者失败？**

```javascript
onerror
<element onerror="myScript">
object.onerror=()=>{myScript};
```

1. **js 函数节流**

    >

---

### JS 场景

1. **使（a==1 && a==2 && a==3）结果为 true**

    ```javascript
    defineProperty
    defineProperties
    valueOf
    toString
    ```

1. **有数组[1, 2, 3, 4, 5, 6, 7, 6, 5, 4, 3, 2, 1]， 最快的去重方法**

    > Set
    > 循环判断

1. **假设现在有几个数组， 数组中分别有多种字符串标示出来的状态 (比如: ERROR: '错误', SERIOUS: '严重问题', GENERAL: '一般问题', NORMAL: '正常'), 需要分别找出这几个数组中最严重的**状态
    >

---

---

# 框架

---

## VUE

---

1. **vue 双向绑定原理**

    >

1. **简单描述各个生命周期具体适合哪些场景**

    >

1. **如何让 CSS 只在当前组件中起作用**

    >

1. **如何缓存组件避免重新渲染**

    >

1. **组件的作用以及封装 vue 组件的过程**

    >

1. **对 vuex 的看法**

    >

1. **vue 如何实现父子组件通信，以及非父子组件通信**

    >

1. **为什么要选 vue，与其它框架对比的优势和劣势**

    >

1. **如何在 vue 中使用第三方 js 库， 比如 axios**

    >

1. **v-if 和 v-show 的区别**

    >

1. **在使用 vue 的过程中都遇到一些什么样的问题， 踩过什么样的坑**

    >

## React

---

## Angular

---

---

# 构建工具

---

### webpack

1. **webpack 的配置文件一般是哪几部分构成的?如何进行项目打包优化?**

1. **什么是 webpack 和 grunt 和 gulp 有什么不同**

1. **什么是 Loader? 什么是 Plugin?**

    > Loaders 是用来告诉 webpack 如何转化处理某一类型的文件，并且引入到打包出的文件中
    > 实现对不同格式的文件的处理，比如说将 scss 转换为 css，或者 typescript 转化为 js
    > 转换这些文件，从而使其能够被添加到依赖图中
    > loader 是 webpack 最重要的部分之一，通过使用不同的 Loader，我们能够调用外部的脚本或者工具，实现对不同格式文件的处理
    > Plugin 是用来自定义 webpack 打包过程的方式，一个插件是含有 apply 方法的一个对象，通过这个方法可以参与到整个 webpack 打包的各个流程(生命周期)。

1. **如何可以自动生成 webpack 配置？**

    > webpack-cli /vue-cli /etc 脚手架工具

1. **什么是模块热更新？**

    > 模块热更新是 webpack 的一个功能，他可以使得代码修改过后不用刷新浏览器就可以更新，是高级版的自动刷新浏览器。
    > devServer 中通过 hot 属性可以空时模块的热替换

1. **列举几个常见的 loader**

    > file-loader：把文件输出到一个文件夹中，在代码中通过相对 URL 去引用输出的文件
    > url-loader：和 file-loader 类似，但是能在文件很小的情况下以 base64 的方式把文件内容注入到代码中去
    > source-map-loader：加载额外的 Source Map 文件，以方便断点调试
    > image-loader：加载并且压缩图片文件
    > babel-loader：把 ES6 转换成 ES5
    > css-loader：加载 CSS，支持模块化、压缩、文件导入等特性
    > style-loader：把 CSS 代码注入到 JavaScript 中，通过 DOM 操作去加载 CSS。
    > eslint-loader：通过 ESLint 检查 JavaScript 代码

---

---

# 其它

1. **对于前端自动化构建工具有了解,简单介绍一下**

1. **减少页面加载时间的方法,常见的网页性能优化方法**

1. **引起内存泄漏的操作有哪如？**

1. **如果在一年内打算掌握的一项技术是什么**

1. **了解 Node 么?Node 的使用场景都有哪**

1. **工作中遇到的一些问题， 是怎么解决的**

<style>
ol{padding-left: 0;}
</style>
