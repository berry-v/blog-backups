---
title: 问题-CSS
date: 2017-08-17 10:33:14
tags: [面试]
---

CSS相关

<!-- more -->


---
1. **页面渲染流程**
    >

1. **link和@import区别用法**
    >

1. **src和url的区别**
    >

1. **盒子垂直水平居中**
    > 定位 盒子宽高已知， 
        position: absolute; 
        left: 50%; 
        top: 50%; 
        margin-left:-自身一半宽度; 
        margin-top: -自身一半高度;
    table-cell布局 
        父级 
            display: table-cell; 
            vertical-align: middle;  
        子级 
            margin: 0 auto;
    定位 + transform ; 适用于 子盒子 宽高不定时；
        position: relative / absolute;
        /*top和left偏移各为50%*/
        top: 50%;
        left: 50%;
        /*translate(-50%,-50%) 偏移自身的宽和高的-50%*/
        transform: translate(-50%, -50%); 注意这里启动了3D硬件加速哦 会增加耗电量的 （至于何是3D加速 请看浏览器进程与线程篇）
    flex 布局
        display: flex; /*flex 布局*/
        align-items: center; /*实现垂直居中*/
        justify-content: center; /*实现水平居中*/
    水平方向上居中
        margin-left : 50% ; transform: translateX(-50%);

1. **CSS清除浮动的几种方法(至少两种)**
    > 使用带 clear 属性的空标签
    使用 css 的 overflow 属性
    使用 css 的伪元素:after 和 zoom(zoom 是为了兼容 IE6，7)
    以浮制浮（父级同时浮动）
    给父元素添加 overflow：hidden 清除浮动方法;
    父级设置成 inline-block;
    结尾处加 br 标签 clear:both。

1. **CSS隐藏元素的几种方法(至少说出三种)**
    > display:none; visiblity:hidden; height:0; opacity: 0;

1. **介绍一下CSS的盒子模型?**
    >

1. **列举几个可以继承的和不可继承的 css 属性**
    > 可继承的属性：font-size, font-family, color
    不可继承的样式：border, padding, margin, width, height

1. **画一条0.5px的直线**
    >

1. **画一个三角形？**
    >

1. **css sprite是什么？有什么优缺点？**
    > 概念：将多个小图片拼接到一个图片中。通过background-position和元素尺寸调节需要显示的背景图案。
    优点：
        。减少HTTP请求数，极大地提高页面加载速度
        。增加图片信息重复度，提高压缩比，减少图片大小
        。更换风格方便，只需在一张或几张图片上修改颜色或样式即可实现
    缺点：
        。图片合并麻烦
        。维护麻烦，修改一个图片可能需要从新布局整个图片，样式

1. **calc, support, media各自的含义及用法？**
    >@support主要是用于检测浏览器是否支持CSS的某个属性，其实就是条件判断，如果支持某个属性，你可以写一套样式，如果不支持某个属性，你也可以提供另外一套样式作为替补。
    calc() 函数用于动态计算长度值。 calc()函数支持 "+", "-", "*", "/" 运算；
    @media 查询，你可以针对不同的媒体类型定义不同的样式。

1. **position:absolute和float属性的异同?**
    >共同点：对内联元素设置float和absolute属性，可以让元素脱离文档流，并且可以设置其宽高。
    不同点：float仍会占据位置，absolute会覆盖文档流中的其他元素。

1. **CSS的盒子模型？**
    >（1）两种， IE 盒子模型、标准 W3C 盒子模型；IE 的content部分包含了 border 和 pading;
    （2）盒模型： 内容(content)、填充(padding)、边界(margin)、 边框(border).

1. **介绍一下box-sizing属性？**
    >box-sizing属性主要用来控制元素的盒模型的解析模式。默认值是content-box。
    content-box：让元素维持W3C的标准盒模型。元素的宽度/高度由border + padding + content的宽度/高度决定，设置width/height属性指的是content部分的宽/高
    border-box：让元素维持IE传统盒模型（IE6以下版本和IE6~7的怪异模式）。设置width/height属性指的是border + padding + content
    标准浏览器下，按照W3C规范对盒模型解析，一旦修改了元素的边框或内距，就会影响元素的盒子尺寸，就不得不重新计算元素的盒子尺寸，从而影响整个页面的布局。

1. **如何实现半透明边框？**
    >

1. **圆角边框？**
    >

1. **怎么添加阴影？**
    >

1. **rgba**
    >

1. **谈谈css3动画transform、animation和transition？**
    >

1. **用过它们哪些属性？**
    > transition需要触发一个事件才会随着时间改变其CSS属性
    animation在不需要触发任何事件的情况下，也可以显式的随时间变化来改变元素CSS属性

1. **less？sass？用过哪些？介绍下它们的特性**
    >

1. **demo**
    >
    

---












