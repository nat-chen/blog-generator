---
title: Node.js Server
date: 2018-04-16 06:28:55
tags: Node
---

## TCP 传输控制协议（Transmission Control Protocol）

### HTTP 协议
* 由 TCP 协议和 IP 协议（简称 TCP/IP ）构建

### TCP 与 UDP 区别
* TCP 可靠，面向连接，相对 UDP 较慢
* UDP 不可靠，不面向连接，相对 TCP 较快

### TCP 三次握手
* 每次建立连接前，客户端与服务端之前都要先进行三次对话才开始正式传输内容，内容如下：
  - 客户端：我要连接你了，可以吗
  - 服务端：嗯，我准备好了，连接我吧
  - 客户端：那我连接你了
  - 开始后面步骤


## IP 网络协议 （Internet Protocol）
* IP 分为内网 IP 和外网 IP；内网中的设备可以互相访问，外网中的设备可以互相访问。
* 通过路由的中转，实现内网和外网的互通，路由有时称为 ‘网关’
*  本地 IP: 127.0.0.1，表示设备自己（ping 127.0.0.1 / ping localhost）
* 特殊 IP: 0.0.0.0, 不表示任何设备

## 端口

### 简述
* 访问一个设备，只指定 IP 是不够的，还必须指定端口（Port）。端口是一个编号，并不是一种硬件，一个端口对应一个服务。

### 端口数
* 根据协议规定，每台机器一共有 65535（2^16 - 1）个端口。
* 0 到 1023 （2^10 - 1）号端口是留给系统使用的，只有拥有管理员权限才能使用这 1024 个端口
* 其他端口则给普通用户使用
* 如果一个端口占用，必需停掉正在使用的这个端口服务，才可以指定其他服务
* 在浏览器中输入网址时，浏览器将默认加上端口 80 你 
* 常用端口
  - HTTP：80 
  - HTTPS: 443
  - FTP: 21
  - 代理服务器端口： 1080
  - 3306： 

### 笔记
* 在 HTTP 响应中页面乱码，可能是 setHeader 里未设置 Content-Type 的 charset 为 utf-8
* HTTP 路径不是文件路径！！！/xxx.html 不一定对应 xxx.html 文件

```bash
curl -s -v -- http://qq.com #请求第一行：GET / HTTP/1.1
curl -s -v -- http://qq.com/xxx?name=ff #请求第一行：GET /xxx?name=ff HTTP/1.1
curl -s -v -- http://qq.com/xxx?name=ff #请求的查询参数：?name=ff
```

