---
title: HTTP入门
date: 2018-04-08 22:48:48
tags: HTTP
---

## URI

### 介绍
* 全称为统一资源标识符（Uniform Resource Identifier)
* URI 分为 URL 和 URN，一般使用 URL 作为网址

### URN
* 全称为统一资源名称（Uniform Resource Name）
* ISBN 号便是一个 URN

### URL
* 全称为统一资源定位符（Uniform Resource Locator）
* 完整格式：协议类型:[//[访问资源需要的凭证信息@]服务器地址[:端口号]][/资源层级UNIX文件路径]文件名[?查询][#片段ID]，其中【访问凭证信息@；:端口号；?查询；#片段ID】都属于选填项。
* 实例：https://www.baidu.com/s?wd=hello&rsv_spt=1#5
  - `https://` 协议
  - `www.baidu.com` 域名
  - `/s` 路径
  - `?wd=hello&rsv_spt=1` 查询参数
  - `#5` 锚点

### DNS 
* 全称为域名系统（Domain Name System）
* 流程：1. 输入域名 2. 输出 IP

```bash
nslookup baidu.com
ping baidu.com
```


## 请求与响应

### Server + Client + HTTP
* 浏览器负责发起请求
* 服务器在 80 端口接收请求
* 服务器负责返回内容（响应）
* 浏览器负责下载响应内容
* HTTP 指导浏览器与服务器如何进行沟通

### 请求示例

#### GET 
* 用 curl 创造一个请求，并得到响应：`curl -s -v -H 'nat: xxx' -- 'https://www.google.com'`
* 请求的内容
```bash
> GET / HTTP/1.1
> Host: www.baidu.com
> User-Agent: curl/7.54.1
> Accept: */*
> nat: xxx
```

#### POST
* 请求：`curl -X POST -s -v -H 'nat:xxx' -- 'https://www.baidu.com'
* 请求内容
```bash
> POST / HTTP/1.1
> Host: www.baidu.com
> User-Agent: curl/7.54.1
> Accept: */*
> nat: xxx
```

#### POST 内容
* 请求：`curl -x POST -d '1234567890' -s -v -H 'nat:xxx' -- 'https://www.baidu.com'` 
* 请求内容
```bash
> POST / HTTP/1.1
> Host: www.baidu.com
> User-Agent: curl/7.54.0
> Accept: */*
> nat:xxx
> Content-Length: 10
> Content-Type: application/x-www-form-urlencoded
> 
> 1234567890
```

#### 请求的格式
* 格式
```bash
1 动词 路径 协议/版本
2 Key1: value1
2 Key2: value2
2 Key3: value3
2 Content-Type: application/x-www-form-urlencoded
2 Host: www.baidu.com
2 User-Agent: curl/7.54.0
3 
4 要上传的数据
```
* 请求最多包含四部分，最少包含三部分，也就是第四部分可以为空
* 第三部分永远都是一个回车（\n），意图为隔断第二四部分
* 动词有 GET POST PUT PATCH DELETE HEAD OPTIONS 等
* 路径包括 ‘查询参数’，但不包括 ‘锚点’
* 没写路径时，默认为 `/`，非命令行中的根目录
* 第二部分中 Content-Type 标注了第 4 部分的格式

### 用 Chrome 发起请求
* 打开 Network
* 地址栏输入网址
* 在 Network点击，查看 request，点击 view source，查看请求的前三部分
* 若有请求的第四部分，FormData 与 Payload 里面可以看到

### 响应
* 请求后，除非断网或是服务器宕机了，否则都能得到一个响应

#### 响应格式
```bash
1 协议/版本号 状态码 状态解释
2 Key1: value1
2 Key2: value2
2 Content-Length: 17931
2 Content-Type: text/html
3
4 要下载的内容
```
* 状态码要背，是服务器对浏览器说的话
  - 1xx 不常用
  - 2xx 表示成功
  - 3xx 表示滚吧
  - 4xx 表示你丫错了
  - 5xx 表示好吧，我错了
* 状态解释没什么用
* 第二部分中的 Content-Type 标注了第四部分的格式
* 第二部分中的 Content-Type 遵循 MIME 规范

#### 用 Chrome 查看响应
* 打开 Network
* 输入网址
* 选中第一个响应
* 查看 Request Headers，点击 view source，查看到响应的前两部分
* 查看 Response 或 Preview，看到响应的第 4 部分


### cURL 命令
* 全称为 Command Line URL viewer，一种命令行工具，作用是发出网络请求，然后得到和提取数据。
* 查看网页源码 `curl 'www.baidu.com'`, 可以用 `curl -o [filename] 'www.baidu.com'` 保存网页
* 自动跳转 `curl -L 'www.baidu.com'`
* 显示头信息 `curl -i 'www.baidu.com'`，连同网页一起，`-I` 参数则只显示 http response 的头信息
* 显示一次 http 通信整个过程，包括端口连接和 http request 头信息 `curl -v 'www.baidu.com'`，亦可通过 `curl --trace-ascii output.txt 'www.baidu.com'` 保存并查看更详细的通信过程
* 发送表单信息 
  - GET: `curl example.com/form.cgi?data=xxx`
  - POST: `curl -X POST--data-urlencode "date=April 1" example.com/form.cgi`
* HTTP 动词：curl 默认为 GET，使用 `-X` 参数可以支持其他动词 `curl -X DELETE 'www.example.com'`






