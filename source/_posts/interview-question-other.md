---
title:  问题-其它
date: 2017-08-17 14:05:37
tags: [面试]
---

框架，应用，优化 等

<!-- more -->

---
1. **前端 MV*框架的意义**
    > 早期前端都是比较简单，基本以页面为工作单元，内容以浏览型为主，也偶尔有简单的表单操作，基本不太需要框架。
    随着 AJAX 的出现，Web2.0的兴起，人们可以在页面上可以做比较复杂的事情了，然后前端框架才真正出现了。
    如果是页面型产品，多数确实不太需要它，因为页面中的 JavaScript代码，处理交互的绝对远远超过处理模型的，但是如果是应用软件类产品，这就太需要了。
    长期做某个行业软件的公司，一般都会沉淀下来一些业务组件，主要体现在数据模型、业务规则和业务流程，这些组件基本都存在于后端，在前端很少有相应的组织。
    从协作关系上讲，很多前端开发团队每个成员的职责不是很清晰，有了前端的 MV框架，这个状况会大有改观。
    之所以感受不到 MV*框架的重要性，是因为Model部分代码较少，View的相对多一些。如果主要在操作View和Controller，那当然 jQuery 这类库比较好用了。

1. **优化首屏白屏问题**
    >
1. **http和https的区别**
    >
1. **前端网站有哪些性能优化的方法？**
    >减少HTTP请求：合并文件、CSS精灵、inline Image
    减少DNS查询：DNS查询完成之前浏览器不能从这个主机下载任何任何文件。方法：DNS缓存、将资源分布到恰当数量的主机名，平衡并行下载和DNS查询
    避免重定向：多余的中间访问
    使Ajax可缓存
    非必须组件延迟加载
    未来所需组件预加载
    减少DOM元素数量
    减少iframe数量
    将脚本放到页面底部
1. **webpack的配置文件一般是哪几部分构成的？如何进行项目打包优化？**
    >

1. **对于前端自动化构建工具的了解**
    >

1. **git常见的命令**
    >

1. **demo**
    >

1. **demo**
    >

        
---