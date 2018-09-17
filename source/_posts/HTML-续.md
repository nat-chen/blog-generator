---
title: HTML 续
date: 2018-04-15 07:52:04
tags: HTML
---

## meta 标签
### 概述
* 那些不能由其他 HTML 元相关元素（`base`, `link`, `script`, `title` 或 `style`）之一表示的任何元数据信息

### 属性
* `charset`：当前文档所使用的字符编码，但该声明可以被任何一个元素的 lang 特性的值覆盖。鼓励使用 UTF-8
* `http-equiv`：定义能改变服务器和用户引擎行为的编译
* `content`：基于内容，为 http-equiv 或 name 属性提供了与其相关的值的定义

```html
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
```


## iframe 标签
### 概述
* 表示嵌套的浏览上下文，有效地将另一个 HTML 页面嵌入到当前页面中。每个浏览上下文都有自己的会话历史记录和活动文档

### 属性
* `frameborder`：默认值为 1，告诉浏览器在当前 iframe 与其他 iframe 之间绘制边框，取 0 时则无需绘制边框
* `height/width`：以 CSS 像素格式，或百分比格式指定 frame 的高度
* `name`：嵌入的浏览上下文（框架）的名称。该名称可以用作 `a` 标签，`form` 标签的 target 属性值，或是 `input` 标签和 `button` 标签的 formtarget 属性值
* `src`：嵌套页面的 URL 地址

```html
<iframe name="xxx" src="#" frameborder="0"></iframe>
<a target="xxx" href="http://qq.com">QQ</a>
```

## a 元素
### 概述
* 即锚元素，创建一个到其他网页，文件，同一页面内的位置，电子邮件地址或任何其他 URL 的超链接。
* 跳转到其他页面，使用 GET 请求

### 属性
* `download`：指示浏览器下载 URL 而不是导航到 URL，将提示用户将其保存为本地文件。如果属性有个值，它将在保存提示中用作预先填写的文件名。
* `href`：**必需**，为锚定义一个超文本链接来源，使用 ‘#top’ 或是 “#” 属性值返回到页面顶部。
  - 属性值为 "qq.com", 被当成文件 qq.com
  - 属性值为 "//qq.com，浏览器会根据当前协议，补全无协议链接的协议；如果用 file:// 协议浏览页面，就会访问到 file://qq.com，这是一个不存在的路径；尽量不使用 file:// 协议预览网页，以免无协议链接出错
  - 属性值为 "?name=nat", 发起请求自动加入页面地址尾部
  - 属性值为 "javascript:alert('hi');", JS 伪协议
  - 属性值为 "" 时，将刷新自身页面，最好使用 `href="javascript:;`
  - 属性值为 "#"时，页面滚到顶部，锚点变为 #
  - 属性值为 "/.."时，当标签被点击时浏览器发起 GET / HTTP/1.1 的请求
* `rel`：指定了目标对象到链接对象的关系
* `target`：指定在何处显示链接的资源：
  - `_self`：当前页面加载
  - `_blank`：新窗口打开
  - `_parent`：加载响应到当前框架的父框架或当前的父浏览上下文
  - `_top`：加载响应进入顶层浏览上下文
  > 使用 target 时，考虑添加 rel="noopener norefferrer" 以防止针对 window.opener API 的恶意行为
  - `name`: **过时**，在页面中定义锚点的目标位置是必须的。在 HTML5 中使用全局属性 id 来代替
 

## form 标签
### 概述
* 表示文档中的一个区域，包含有交互控制元件，用于向 web 服务器提交信息

### 属性
* `action`：处理 form 信息的程序所在的 URL
* `autocomplete`：指示 input 元素是否能够拥有一个默认值，这个默认值是由浏览器自动补全的。
* `enctype`：当 method 属性值为 post 时，enctype 是提交 form 给服务器的内容的 MIME 类型，这个值可以被 `button` 或 `input` 元素中 `fromenctype` 属性重载
  - `application/x-www-form-urlencoded`：如果属性未指定时的默认值
  - `multipart/form-data`：这个值用于一个 type 属性设置为 "file" 的 input 元素
  - `text/plain`：HTML5
* `method`：使用这种 HTTP 方式来提交 form，这个值可以被 `button` 或 `input` 元素中 `fromenctype` 属性重载
  - `post`：HTTP 的 POST 方法，表单数据会包含在表单体内然后发送给服务器
  - `get`：HTTP 的 GET 方法，表单数据会附加在 action 属性的 URI 中，并以 '?' 作为分隔符，以这种形式的 URI 再发送给服务器（数据暴露在 URI 里面）
* `name`：**不推荐**，form 名字，HTML5 中一个文档中的多个 form 当中，name 必须唯一而不仅仅是一个空字符串
* `target`：指示在提交表单之后，在哪里显示收到的回复：`_self`, `_blank`, ` _top`, `_parent` 或是 iframename（指定 frame 中加载），这个值可以被 `button` 或 `input` 元素中 `fromenctype` 属性重载

## 总结笔记
* 不含 submit 类型按钮将无法提交
* form 标签里面有个 input type=submit 的元素或是有一个 button 元素，而 type 属性为 空
* form 标签里面的 input 不加 name 属性时，input 值不会出现在请求里
* file 协议不支持 post 请求
* `tfoot/thead/tbody` 页面排序显示与 HTML 排版无关

```bash
npm i -g http-server
http-server -c-1 #不保留缓存
```

```html
<!-- form 使用 -->
<form action="users" method="post">
  <input type="text" name="username">
  <input type="password" name="password">
  <input type="submit" value="提交">
</form>

<!-- input 与 label 使用1 -->
<input type="checkbox" id="select">
<label for="select">ok</label>

<!-- input 与 label 使用2 -->
<label>username
	<input type="text" name="xxx">
</label>

<!-- input 其他用例 -->
<input type="checkbox" name="fruit" value="orange">橙子
<input type="checkbox" name="fruit" value="banana">香蕉

<input name="select" type="radio" value="yes">Yes
<input name="select" type="radio" value="no">No

<!-- select 用例 -->
<select name="group" multiple>
  <option value="">--</option>
  <option vlaue="1" disabled>1</option>
  <option value='2' selected>2</option>
  <option value='3'>3</option>
</select>

<!-- textarea 用例 -->
<textarea style="resize: none" cols=10 row=20 name="hobby"></textarea>

<!-- table 用例 -->
<table border=1 style="border-collapse: collapse">
  <colgroup>
    <col width=100>
    <col bgcolor=red width=200>
    <col width=100>
    <col width=70>
  </colgroup>
  <thead>
    <tr>
      <th>项目</th><th>姓名</th><th>班级</th><th>分数</th>
    </tr>
  <thead>
  <tbody>
    <tr>
      <th></th><td>小明</td><td>1</td><td>94</td>
    </tr>
    <tr>
      <th></th><td>小红</td><td>2</td><td>96</td>
    </tr>
    <tr>
      <th>平均分</th><td></td><td></td><td></td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th>总分</th><td></td><td></td><td>190</td>
    </tr>
  </tfoot>
</table>
```













