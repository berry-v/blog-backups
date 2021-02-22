---
title: 神奇的运算符
date: 2017-07-27
tags: [小技巧, JavaScript]
---

运算符不止于判断、计算

<!-- more -->

## 阿啵呲嘚
话说，突然想了解位运算，于是， 查询了一些资料。 
了解到平时的数值运算其实是要先转换为二进制再进行运算， 而位运算是直接进行二进制运算的。所以， 厉害了～ ～ ～

## &按位与
&与&& 类似， 条件都为true时， 才为true
例：运算时 二进制位数比对， 都为1时才为1
<table><tr><td></td><td>十进制 / 二进制</td><td>十进制 / 二进制</td><td>十进制 / 二进制</td><td>十进制 / 二进制</td><td>十进制 / 二进制</td></tr><tr><td></td><td>1/0001</td><td>1/0001</td><td>2/0010</td><td>3/0011</td><td>5/0101</td></tr><tr><td></td><td>2/0010</td><td>3/0011</td><td>3/0011</td><td>4/0100</td><td>6/0110</td></tr><tr><td>&</td><td>0/0000</td><td>1/0001</td><td>2/0010</td><td>0/0000</td><td>4/0100</td></tr></table>

且 十进制转换为二进制后， 末位数为1即奇数， 末位数为0即偶数。
所以可以用一个数和1进行按位&来判断是否为偶数
```javaScript
function assert(n) {
  return n&1 ? '奇数' : '偶数';
}
```

## |按位或
|与|| 类似， 其中一个为true的时候结果就为true
<table><tr><td></td><td>十进制 / 二进制</td><td>十进制 / 二进制</td><td>十进制 / 二进制</td><td>十进制 / 二进制</td><td>十进制 / 二进制</td></tr><tr><td></td><td>1/0001</td><td>1/0001</td><td>2/0010</td><td>3/0011</td><td>5/0101</td></tr><tr><td></td><td>2/0010</td><td>3/0011</td><td>3/0011</td><td>4/0100</td><td>6/0110</td></tr><tr><tr><td>|</td><td>3/0011</td><td>3/0011</td><td>3/0011</td><td>7/0111</td><td>7/0111</td></tr></table>

由于浮点数不支持位运算， 所以自动转换为整数， 再进行运算。 
因为这个特性， 可以取巧， 用来做向下运算（math.floor）
```javaScript
console.log(1.23|0); //1
```
<!-- ## ~ 按位非
<table><tr><td></td><td>十进制 / 二进制</td><td>十进制 / 二进制</td><td>十进制 / 二进制</td><td>十进制 / 二进制</td><td>十进制 / 二进制</td></tr>
<tr><td></td><td>1/0001</td><td>2/0010</td><td>3/0011</td><td>4/0100</td><td>5/0101</td></tr>
<tr><td>～</td><td>14/1110</td><td>13/1101</td><td>12/1100</td><td>11/1011</td><td>10/1010</td></tr></table> -->

还有更多的， 之后再说

## &&
&& 当&&之前的条件为 true 时执行&&之后的代码。

### 用例
#### && 用于简短的判断 
```javaScript
  let name = document.getElementById('name');
  name && clearValue(name); // 条件为真 方法执行
  function clearValue(input){
    input.value='';
  }
```

## ||
|| 当||之前的条件为 false 时执行&&之后的代码。

### 用例
#### 判断变量是否定义， 没有定义则赋一个初始值
var num = num || 0;

## || & &&
### 简化switch
```javaScript
  let condition = Math.ceil(Math.random()*5), color;
  switch (condition) {
    case 0:
      color = '红艳艳';
      break;
    case 1:
      color = '黑乎乎';
      break;
    case 2:
      color = '黄灿灿';
      break;
    case 3:
      color = '绿油油';
      break;
    default:
      color = '五颜六色';
      break;
  }
```
等于
```javaScript
  let condition = Math.ceil(Math.random()*5);
  let color = (condition==0 &&  '红艳艳') || (condition==1 &&  '黑乎乎') || (condition==2 &&  '黄灿灿') || (condition==3 &&  '绿油油') || '五颜六色';
```
等于
```javaScript
  let condition = Math.ceil(Math.random()*5);
  let color = {'0': '红艳艳', '1': '黑乎乎', '2': '黄灿灿', '3': '绿油油'}[condition] || '五颜六色';
```
完美～～～


之后发现了再补～ ～ ～