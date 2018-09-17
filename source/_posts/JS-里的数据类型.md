---
title: JS 里的数据类型
date: 2018-05-22 19:45:52
tags: 基础
---

## 数据类型
* 简单数据类型: Undefined, Null, Boolean, Number, String, Symbol;
* 复制数据类型: Object

## Undefined 类型
* 只有一个值, 即 `undefined`, 表未声明或未初始化
```js
var a; // a 的值为 undefined
```

## Null 类型
* 只有一个值, 即 `null`, 表空对象指针,即表示未指向任何对象
```js
var a = null;
```

## Boolean 类型
* 值为: `true` 和 `false`
* 所有为 false 的值: `false`, 空字符, 0, `NaN`, `null`, `undefined` 
```js
var bool_1 = new Boolean(true);
var bool_2 = true
```

## Number 类型
* 使用 IEEE754 格式表示整数和浮点数值
* 进制:
  * 二进制: `0b1`;
  * 八进制: `0o1`;
  * 十进制: `1`;
  * 十六进制: `0x1`;
```js
var num_1 = new Number(1);
var num_2 = 1
```

## String 类型
* 由 0 或多个 16 位 Unicode 字符组成的字符序列
```js
var str_1 = new String('a');
var str_2 = 'a'
```

## Object 类型
* 又称为引用类型, 是一种数据结构, 用于将数据和功能组织在一起.
```js
var obj_1 = new Object();
var obj_2 = {};
```

## 浅复制
* 对象间的浅复制: 仅对对象地址的复制
```js
var obj = { a:1, arr: [2,3] };

var shadowCopy = function(obj) {
  var copy = {};
  for (var key in obj) {
    if (obj.hasOwnProperty(key)) {
      copy[key] = obj[key]; //复制一层, 仅地址
    }
  }
};
```

## 深复制
* 基本类型值的间的值复制
* 对象间的深复制通过递归层层开辟新的栈
```js
//基本类型
var num_1 = 5;
var num_2 = num_1;

//对象
var obj = { 
  a: 1,
  b: {
    c: {
      2
    }
  }
};

var deepCopy = function(obj) {
  var copy = {};
  for (var key in obj) {
    if (obj.hasOwnProperty(key)) {
      var value = obj[key];
      if (Object.prototype.toString.apply(value) === '[object Object]') {
        copy[key] = deepCopy(value);
      } else {
      copy[key] = value;      
      }
    }
  }
  return copy;
};
```
