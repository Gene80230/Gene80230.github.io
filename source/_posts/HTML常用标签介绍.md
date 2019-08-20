---
title: HTML标签介绍
date: 2019-08-18 23:36:17
tags:
---
这一节的笔记只是先介绍下HTML常见标签，重点需要学习的标签将会在下一节介绍讲解。
### HTML常用标签介绍
**&lt;!DOCTYPE html&gt; HTML文档类型声明**
或许有人会有疑惑写在网页开头的这个声明，它的作用到底是什么呢？
其实它是用来**选择文档类型的**，在html历史上有很多文档的类型声明，这是现如今最简单的一个文档声明。其他的文档类型声明，[请点击这里](https://www.w3.org/QA/2002/04/valid-dtd-list.html)

### 常见标签/元素 (括号内是其全称及翻译)
`a (anchor 锚点)`
`form`
`input`
`button (按钮)`
`h1~h6 (标题)`
`p (pargraph 段落)`
`ul (un-ordered list 无序列表)`
`ol (ordered list 有序列表)`
`small`
`strong`
`div`
`span`
`kbd (键盘按键)`
`video (视频)`
`audio (音频)`
`svg (可缩放的矢量图形)`
`dl (description list    描述列表) `
`dt (description term        项目) `
`dd (description definition  项目描述) `
除了`div`和`span`标签,其他标签都有默认样式。

### 元素类型
- **块状元素（block）：**效果上会独占一行的标签。
- **内联元素（inline）：**和其它的元素放在一起,不会独占一行。

### 列表元素
1. 无序列表 ul（unorder list） 典型的块状元素，并且ul还有margin，在不同的浏览器中margin是不同的。
 a.列表项： li (list item) 典型的块状元素.
2. 有序列表 ol(order list ) 典型的块状元素，也有margin，在不同的浏览器中margin也是不同的。
 a.列表项： li (list item) 典型的块状元素.
3. 定义列表 dl (definition list) 典型的块状元素
 a. dd (definition detail) 类型详情 典型的块状元素.
 b. dt (definition type) 类型定义 典型的块状元素.

### HTML常用转义字符（括号内是其表示方法）
`< (&lt;) `
`> (&gt;) `
`空格 (&nbsp;) `
`© (&copy;) `
`® (&reg;) `
`™ (&trade;) `

[更多转义字符](http://tool.oschina.net/commons?type=2)

### 文本样式标签
`<b></b>` 加粗标签，样式标签，bold的缩写，内联元素。
`<strong></strong>` 语气强调标签，虽然效果与`b`标签相同，但更加表示强调，而不是`b`标签的加粗。
`<strong></strong>` 语义上的强调，内联元素。
`<i></i>` italic的缩写，内联元素，文本斜体显示，内联元素 。
`<em></em>` 也是斜体的表示，在html中推荐使用其来代替i标签,emphasize缩写为em,内联元素。
`<h1~6></h1~6>` 描述语义的标签，块状元素，从上到下字体大小依次减少。
`<p></p>` paragraph的缩写，描述的是语义，段中没有间距，但是在段与段之间是有间距的，但是margin在不同的浏览器中是一样的，典型的块状元素。
`<br>` 空元素（概念在下面）,输出换行。
`<hr>` 空元素 hr: horizontal rule的缩写，分割线 ，常用的属性有`color`、`width`、`align`（对齐方式） 其中`align`有三个选项：`left`、`right`、`center`。


### 空元素
即元素中不能有子元素或其他内容
如 `img` `input` `link` `meta` `hr` `br`

### 可替换元素
如 `img`标签中的`src`属性可用图片的内容替换掉`img`标签，像这种标签被称为可替换元素，大部分是自带宽高的元素

### noscript 标签
如果用户浏览器不支持 script，则会显示`noscript`中的内容