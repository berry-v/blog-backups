---
title: 问题-VUE
date: 2017-08-17 10:11:23
tags: [面试]
---

VUE 相关

<!-- more -->



---

1.  **v-for和v-if的优先级**

    > 当它们处于同一节点，v-for的优先级比v-if更高，这意味着 v-if将分别重复运行于每个 v-for循环中。所以这两个指令最好不要同时使用
    > 解决办法：computed


1. **VUE双向绑定源理**
    >采用数据劫持结合发布者-订阅者模式的方式，通过Object.defineProperty()来劫持各个属性的setter，getter，在数据变动时发布消息给订阅者，触发相应的监听回调。
    第一步：需要observe的数据对象进行递归遍历，包括子属性对象的属性，都加上 setter和getter
    这样的话，给这个对象的某个值赋值，就会触发setter，那么就能监听到了数据变化
    第二步：compile解析模板指令，将模板中的变量替换成数据，然后初始化渲染页面视图，并将每个指令对应的节点绑定更新函数，添加监听数据的订阅者，一旦数据有变动，收到通知，更新视图
    第三步：Watcher订阅者是Observer和Compile之间通信的桥梁，主要做的事情是:
        1、在自身实例化时往属性订阅器(dep)里面添加自己
        2、自身必须有一个update()方法
        3、待属性变动dep.notice()通知时，能调用自身的update()方法，并触发Compile中绑定的回调，则功成身退。
    第四步：MVVM作为数据绑定的入口，整合Observer、Compile和Watcher三者，通过Observer来监听自己的model数据变化，通过Compile来解析编译模板指令，最终利用Watcher搭起Observer和Compile之间的通信桥梁，达到数据变化 -> 视图更新；视图交互变化(input) -> 数据model变更的双向绑定效果。
        
1. **怎么让 一个数组中只改变一个值，不去重新渲染整个数组，而是仅仅只渲染 改变的那一个**
    >

1. **各个生命周期具体适合哪些场景**
    >生命周期钩子的一些使用方法：
    beforecreate : 可以在这加个loading事件，在加载实例时触发
    created : 初始化完成时的事件写在这里，如在这结束loading事件，异步请求也适宜在这里调用
    mounted : 挂载元素，获取到DOM节点
    updated : 如果对数据统一处理，在这里写上相应函数
    beforeDestroy : 可以做一个确认停止事件的确认框
    nextTick : 更新数据后立即操作dom

1. **如何让CSS只在当前组件中起作用?**
    >将当前组件的&lt;style&gt;修改为&lt;style scoped&gt;

1. **如何缓存组件避免重新渲染？**
    >&lt;keep-alive&gt;&lt;/keep-alive&gt; 会缓存不活动的组件实例,主要用于保留组件状态或避免重新渲染。

1. **封装 vue 组件的过程？**
    >首先，组件可以提升整个项目的开发效率。能够把页面抽象成多个相对独立的模块，解决了我们传统项目开发：效率低、难维护、复用性等问题。
    然后，使用Vue.extend方法创建一个组件，然后使用Vue.component方法注册组件。子组件需要数据，可以在props中接受定义。而子组件修改好数据后，想把数据传递给父组件。可以采用emit方法。

1. **你是怎么认识vuex的？**
    >vuex可以理解为一种开发模式或框架
    通过状态（数据源）集中管理驱动组件的变化
    应用级的状态集中放在store中； 改变状态的方式是提交mutations，这是个同步的事物； 异步逻辑应该封装在action中。

1. **vue-loader是什么？使用它的用途有哪些？**
    >解析.vue文件的一个加载器，跟template/js/style转换成js模块。
    用途：js可以写es6、style样式可以scss或less、template可以加jade等

1. **vue如何实现父子组件通信，以及非父子组件通信？**
    >props
    $emit
    $on

1. **如何在vue中使用第三方js库， 比如axios**
    >

1. **v-if和v-show的区别**
    >

1. **vuex 是什么？怎么使用？哪种功能场景使用它？vuex 的 getter 特性是什么？(对 vuex 的看法)**
    >
    
1. **为什么要选vue？与其它框架对比的优势和劣势？**
    >

---