---
title: web历史以及HTTP请求
date: 2019-08-17 21:54:25
tags:
---
### WWW的历史
1989年-1992年，Tim Berners-Lee（李爵士）发明了www（world wride web）一种适用于全世界的网络。除此之外他还发明了第一个服务器、第一个浏览器、第一个网页。

主要包含：
- URI（统一资源标识符），俗称网址
- HTTP，电脑之间传输内容的协议
- HTML，超级文本，用来做页面跳转

作用：
URI能让你访问一个页面，HTTP能让你下载这个页面，HTML能让你看懂这个页面

**URI是什么**
URI分为URL（统一资源定位符）和URN（统一资源名称），我们一般使用URL作为网址

**URL**
我们可以通过URL确定一个唯一的网址
![Image.png](https://i.loli.net/2019/08/17/uSURxEL32iKYkwA.png)

#### DNS & hosts
**DNS**
域名解析，输入域名，输出IP

我们可以用 nslookup baidu.com，来通过路由器查询百度对应的IP
![Image _2_.png](https://i.loli.net/2019/08/17/kQtHAjIg7iDlJpy.png)

或者是ping一下
![Image _3_.png](https://i.loli.net/2019/08/17/GbPjhi85gsL2VuF.png)


### 服务器（Server）、客户端（Client）、HTTP
#### 服务器与客户端
每一个电脑都有端口 每一个端口都有唯一的功能

21  是FTP协议 用于email
443 是FTPS协议
1080 是代理服务器端口
3306 是MySQL服务器
80 是HTTP协议

#### HTTP
**HTTP 基本概念**
HTTP，全称为HyperText Transfer Protocol，即为超文本传输协议。是互联网应用最为广泛的一种网络协议，所有的 www 文件都必须遵守这个标准。
HTTP 定义了在与服务器交互的不同方式，最常用的方法有 4 种，分别是 GET，POST，PUT， DELETE。URL 全称为资源描述符，可以这么认为：一个 URL 地址，对应着一个网络上的资源，而 HTTP 中的 GET，POST，PUT，DELETE 就对应着对这个资源的查询，修改，增添，删除4个操作。

**HTTP的作用**就是指导浏览器和服务器如何进行沟通（http的详细说明）
1. 如输入网址时错误，服务器会返回一个404
2. 如发送请求到服务器，但是服务器关机或者故障，http会让你响应一个502

HTTP 特性：
-HTTP 是无连接无状态的
-HTTP 一般构建于 TCP/IP 协议之上，默认端口号是 80

HTTP 可以分为两个部分，即请求和响应。
#### 请求和响应
我们先来看请求怎么发送
[curl用法](https://blog.csdn.net/liitdar/article/details/80684730)
**用curl传输数据（get）**
curl -s -v -H "Gene:111" -- "https://www.baidu.com"

只需要看`>`这个符号右侧的内容
比如上面的命令发送出去之后返回一个页面数据如下
```
> GET / HTTP/1.1
> Host: www.baidu.com
> User-Agent: curl/7.55.0
> Accept: */*
> Gene:111
>
```
> GET / HTTP/1.1
GET 获取数据    /  路径是根目录 协议是HTTP和协议的版本号

> User-Agent: curl/7.55.0
> 用的什么软件发起的响应和版本号

> Accept: \*/*
> 接收返回的任何数据

> Gene:111
> 这是用来演示的句子，可加可不加

**用普通 post 上传数据**

```
> POST / HTTP/1.1
> Host: www.baidu.com
> User-Agent: curl/7.55.0
> Accept: */*
> Frank:xxx
>
```

**用带数据的 post 上传数据**
```
> POST / HTTP/1.1
> Host: www.baidu.com
> User-Agent: curl/7.55.0
> Accept: */*
> Frank:xxx
> Content-Length: 10
> Content-Type: application/x-www-form-urlencoded
>
> 1234567890
```

由上面可总结出请求的格式
#### 请求的格式

>1 动词 路径 协议/版本
2 Key1: value1
2 Key2: value2
2 Key3: value3
2 Content-Type: application/x-www-form-urlencoded
2 Host: www.baidu.com
2 User-Agent: curl/7.54.0
3 
4 要上传的数据

- 请求最多包含四部分，最少包含三部分。（也就是说第四部分可以为空）
- 第三部分永远都是一个回车（\n）用于区分第2部分和第4部分
- 动词有 GET(获取) POST(上传) PUT(整体更新) PATCH(部分更新) DELETE(删除) HEAD OPTIONS 等
- 这里的路径包括「查询参数」，但不包括「锚点」
- 如果你没有写路径，那么路径默认为 /
- 第 2 部分中的 Content-Type 标注了第 4 部分的格式

这里还要额外提下get与post的区别
**get与post的区别**
- get为获取内容，在输入网址的时候get
- post为上传内容，如登录的时候post

#### 响应的格式

>1 协议/版本号状态码状态解释
2 Key1: value1
2 Key2: value2
2 Content-Length: 17931
2 Content-Type: text/html
3
4 要下载的内容

#### 状态码
- 状态码要背，是服务器对浏览器说的话
    - 1xx 不常用
    - 2xx 表示成功   200 get成功 204 创建成功
    - 3xx 表示滚吧   301 永久搬走(不存在) 302 临时搬走，还会回来
    - 4xx 表示你丫错了   404 访问者出错
    - 5xx 表示好吧，我错了   502 错误网关
- 状态解释没什么用
- 第 2 部分中的 Content-Type 标注了第 4 部分的格式
- 第 2 部分中的 Content-Type 遵循 MIME 规范


#### 用浏览器查看响应
在network下查看对应网页的响应
![Image _4_.png](https://i.loli.net/2019/08/17/eu7jq5oAp1rWnDL.png)