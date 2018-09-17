---
title: JS 基础
date: 2018-05-20 23:02:53
tags: 基础
---

## 多行字符串
```js
// 方法 1
var str = '123\
  456'; 

// 方法 2
var str = `123
  456`;
```

## 对象的键值
* 键值可以不带引号, 前提是符合标识符命名规范; 如 `var obj = { '9a': 'hi' }` 必须用引号包裹.

## Base64
* 全局函数 `btoa()` 将字符串转为 Base64 编码
* 全局函数 `atob()` 将 Base64 编码转为原来的编码
* 将非 ASCII 码字符转为 Base64 编码, 中间必须先插入一个转码环节
```js
var base = btoa(encodeURIComponent('陈'));
var str = encodeURIComponent(atob(base));
```

## 检验变量是否声明
* 通过 `a in window` 返回 `true/false` 判断
* 直接使用 window.a 需要考虑 a 为显示赋值为 `undefined` 的情况

## 字符串转数字
* `'1.23' - 0`
* `+ '-1'`

## 数字转字符
* `1..toString()` 结果为 '1', 第一个点视为小数位;
* `1.toString()` 结果为 报错;

## 内存图
* 你买一个 8G 的内存条
* 操作系统开机即占用 512MB
* Chrome 打开即占用 1G 内存
* Chrome 各每个网页分配一定数量的内存
* 这些内存要分给页面渲染器、网络模块、浏览器外壳和 JS 引擎（V8引擎）
* JS 引擎将内存分为代码区和数据区
* 我们只研究数据区
* 数据区分为 Stack（栈内存） 和 Heap（堆内存）
* 简单类型的数据直接存在 Stack 里
* 复杂类型的数据是把 Heap 地址存在 Stack 里

## 深复制与浅复制
* 简单类型的数据，赋值就是深拷贝
* 复杂类型的数据（对象），区分浅拷贝和深拷贝

## 变量提升
```js
/*
拆分成如下
var a;
a = { self: a };
*/
var a = { 
  self: a
};
console.log(a) // { self: undefined }


var a = {
  n: 1
};
var b = a;
a.x = a = { n = 2 }; //a. 第一个 a 指向对象 { n : 1 }, b. 先执行 a = { n = 2 };
console.log(a.x) // undefined
console.log(b.x) // { n: 2 }
```

## 全局对象 window
* ECMAScript 规定全局对象叫做 global，但是浏览器把 window 作为全局对象.
* window 的属性就是全局变量, 分为两种:
  * 一种是 ECMAScript 规定的
    * global.parseInt
    * global.parseFloat
    * global.Number
    * global.String
    * global.Boolean
    * global.Object
  * 一种是浏览器自己加的属性
    * window.alert
    * window.prompt
    * window.comfirm
    * window.console.log
    * window.console.dir
    * window.document
    * window.document.createElement
    * window.document.getElementById

## 垃圾回收
* 一个对象没有被引用, 将会被回收

## 原型链
```js
// 重要公式
var 对象 = new 函数();
对象.__proto__ === 函数.prototype;

// 实例
var num = new Number('1');
num.__proto__ === Number.prototype;
num.__proto__.__proto__ = Object.prototype;

Object.__proto__ === Function.prototype; //Function 是 Object 的构造函数
Object.__proto__.__proto__ === Object.prototype;

Function.prototype.__proto__ === Object.prototype // Function.prototype 为对象

Function.__proto__ === Function.prototype; //Function 为函数
Number.__proto__ === Function.prototype;

Objects.prototype.__proto__ === null 
```
