---
title: HTML标签介绍
date: 2019-08-18 23:36:17
tags:
---
这一节的笔记只是先介绍下HTML常见标签，重点需要学习的标签将会在下一节介绍讲解。
### HTML常用标签介绍
**<!DOCTYPE html> HTML文档类型声明**
或许有人会有疑惑写在网页开头的这个声明，它的作用到底是什么呢？
其实它是用来**选择文档类型的**，在html历史上有很多文档的类型声明，这是现如今最简单的一个文档声明。其他的文档类型声明，[请点击这里](https://www.w3.org/QA/2002/04/valid-dtd-list.html)

#### 常见标签
`a (anchor)`
`form`
`input`
`button`
`h1`
`p (pargraph)`
`ul (un-ordered list)`
`ol (ordered list)`
`small`
`strong`
`div`
`span`
`kbd`
`video`
`audio`
`svg`
`dl (description list    描述列表) `
`dt (description term        词语) `
`dd (description definition  定义) `
除了`div`和`span`标签,其他标签都有默认样式。

**空元素**
即元素中不能有子元素或其他内容
如 img input link meta hr br

**可替换元素**
如 img标签中的src属性可用图片的内容替换掉img标签，像这种标签被称为可替换元素，大部分是自带宽高的元素

**noscript 标签**
如果用户浏览器不支持 script，则会显示 noscript 中的内容