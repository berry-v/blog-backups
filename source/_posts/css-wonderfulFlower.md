---
title: 关于CSS的奇葩二三事
date: 2017-07-11 14:50:04
tags: [CSS, 奇葩]
---

关于css的很奇葩的但又不得不去这样写的写法~ ~ ~ ~

<!-- more -->
---
1. **css属性遇到特殊符号**
    > 场景: 某天, 隔壁同桌在使用bugzilla这个开源系统搭建属于自己的bug系统的时候发现, 自动生成的class中是有特殊字符的,  当要去根据这个class书写css的时候, 发现一个问题, class中不能用特殊字符~~. 像是test_(special)这种就不能使用.
    解决办法:使用转义符转义.

    ```html
    <div class="test_(special)"></div>
    ```
    ```css
    .test_\(special\){}
    ```

---