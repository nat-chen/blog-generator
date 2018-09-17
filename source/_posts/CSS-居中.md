---
title: CSS 居中
date: 2018-05-05 14:36:30
tags: CSS 居中
---

## 水平居中

### 内联元素
* 在父级块级元素, 使用 `text-align`
* 适用于 inline, inline-block, inline-table, inline-flex.

```css
.center-children {
  text-align: center;
}
```

### 一个块级元素
* 元素的宽度固定的前提下, 使用 `margin: auto`
```css
.center-me {
  margin: 0 auto; /*margin-left: auto; margin-right: auto*/
}
```

### 多个块级元素
* 将块级元素设置为 `display: inline-block`
```css
/* 元素高度不一 */
.parent {
  text-align: center;
}

.children {
  display: inline-block;
}
```
* 使用 flex 布局
```css
/* 元素高度一致 */
.parent {
  display: flex;
  justify-content: center;
}
```

## 垂直居中

### 内联元素
#### 单行
* 父元素处使用 line-height 等于 height
```css
.center-text {
  height: 100px;
  line-height: 100px;
  white-space: nowrap;
}
```
#### 多行
* 使用 `display: table` 及 `vertical-align: middle`
```css
.center-table {
	display: table;
	height: 250px;
	width: 240px;
}

.center-table p {
	display: table-cell;
	margin: 0;
	vertical-align: middle;
}
```

* flex 属性
```css 
.flex-center-verticallly {
  display: flex;
  justify-content: center;
  flex-direction: column;
  height: 400px; /*父元素的固定宽度不可省*/
}
```

* full-height 伪元素
```css
.ghost-center {
  position: relative;
}
.ghost-center::before {
  content: ' ';
  display: inline-block;
  height: 100%;
  width: 1%;
  vertical-align: middle;
}
.ghost-center p {
  display: inline-block;
  vertical-align: middle;
}
```

### 块级元素
#### 固定高度
```css
.parent {
  position: relative;
}

.child {
  position: absolute;
  top: 50%;
  height: 100px;
  margin-top: -50px; /*account for padding and border if not using box-sizing: border-box; */
}
```

#### 不固定高度
```css
.parent {
  position: relative;
}

.child {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
}
```

#### flex
```css
.parent {
  display: flex;
  flex-direction: column;
  justify-content: center;
}
```

## 垂直水平居中
### 固定高度与宽度
* 绝对定位
```css
.parent {
  position: relative;
}

.child {
  width: 300px;
  height: 100px;
  padding: 20px;
  position: absolute;
  top: 50%;
  left: 50%;
  margin: -70px 0 0 -170px;
}
```

### 未知高度与宽度
```css
.parent {
  position: relative;
}

.child {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%)
}
```

### flex
```css
.parent {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

### grid
```css
/* 仅适用于一个元素 */
body, html {
  height: 100%;
  display: grid;
}
span {
  margin: auto;
}
```








