<!--
 * @Author: baiwei
 * @Date: 2019-02-18 10:58:06
 * @LastEditors: baiwei
 * @LastEditTime: 2021-02-22 13:36:51
 * @Description: 描述
 * @Copyright: Cloud-Star. Co. Ltd. All rights reserved.
-->
---
title: 关于js的模板字符串, es6-templateLiterals
date: 2017-07-06 17:51:34
tags: [JavaScript, ES6]
---

更优雅的字符串拼接
<!-- more -->

模板字符就是允许在字符串中嵌入表达式, 前后使用\`\`来代替"" 和 '' , 然后用${}来嵌入表达式或者变量(注, 如果要在模板字符串内使用反引号\`, 需要用\转义), 可以再字符串中直接换行, 不用写转义的换行符.
比如 \`${name} 长得真好看\`

## 使用表达式
可以在字符中直接使用表达式 看起来比+运算符来得更美腻和优雅
如
```javaScript
var name = '陆小果';
var tag = '我的字典里没有投降两字，因为，因为，我的字典里什么字都没有！';
//字符拼接
console.log('果宝特攻中' + name + '的口头禅是:' + tag);
//模板字符串
console.log(`果宝特攻中${name}的口头禅是:${tag}`);
```

## 标签模板
在模板字符串开始之前加一个额外的标签(这个标签只是一个函数, 通过这个函数的函数名来处理操作这个模板字符)
```javaScript
function template(strings, ...keys){
	return (function(...values){
		var dict = values[values.length - 1] || {};
		var _h = '';
		keys.forEach(function(k, i){
			_h += `${strings[i]}${dict[k]}</br>`;
		});
		return _h;
	});
}
var personal = {
	name: '陆小果',
	age: '18',
	noumenon: '苹果',
	fear: '小伙伴被做成苹果派',
	tag: '我的字典里没有投降两字，因为，因为，我的字典里什么字都没有！'
};
var formatInf = template `姓名: ${'name'} 年龄: ${'age'} 原型: ${'noumenon'} 最害怕的事: ${'fear'} 口头禅: ${'tag'}`;
formatInf(personal);
//姓名: 陆小果</br> 年龄: 18</br> 原型: 苹果</br> 最害怕的事: 小伙伴被做成苹果派</br> 口头禅: 我的字典里没有投降两字，因为，因为，我的字典里什么字都没有！</br>
```

## 实用程度 (例子总结)
有让人眼前一亮的写法的时候再更新...