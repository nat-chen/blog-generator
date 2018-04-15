---
title: HTML 入门
date: 2018-04-10 21:47:58
tags: HTML
---

## W3C
### 简介
* 万维网联盟（World Wide Web Consortium，W3C），又称 W3C 理事会，是万维网的主要国际标准组织。

## MDN
### 简介
* MDN （全称 Mozilla Developer Network）是一个汇集众多 Mozilla 基金会产品和网络技术开发文档的免费网站。

## 空标签
### 简介
* 空标签亦称为空元素 （empty element），可能是 HTML，SVG，或者 MathML 里一个不可能存在子节点的元素。
* 在 HTML 中，通常在一个空元素上使用闭合标签是无效。

### 空元素
`<area>` `<base>` `<br>` `<col>` `<colgroup>` `<command>` `<embed>` `<hr>` `<img>` `<input>` `<keygen>` `<link>` `<meta>` `<param>` `<source>` `<track>` `<wbr>`

## 可替换标签
* CSS 里，可替换元素（replaced element）的展现不是由 CSS 来控制的。这些元素是一类外观渲染独立于 CSS 的外部对象。
* `<img>` `<object>` `<video>` `<textarea>` `<input>` `<audio>` `<canvas>` 和通过 CSS content 属性插入的对象（匿名可替换元素）

## 总结
* 除了 `<div>` 和 `<span>` 外，其他标签都有默认的样式，当然包括 `display: block/inline`.
* `<strong>` 与 `<bold>` 样式一致，但 `<strong>` 含有较强的语气
* 大图一般用 `background` 属性，不用 `<img>`
* HTML 取标签或是 CSS 命名都应由内容而决定，而非样式
* `<hr>` 水平分割符，`<br>` 为强制换行
* `<dl>` = description list，`<dt>` = description term，`<dd>` = description definition，`<ul>` = unordered list，`<ol>` = ordered list，`<li>` = list item
* `whois` 命令为某个域名拥有者的身份
* `<iframe>` 标签
  - 用于在当前页面中嵌入一个页面
  - 它可用拥有一个 name，a 标签的 target 可以通过 name 指向它
  - 现代前端开发中，iframe 很少用




