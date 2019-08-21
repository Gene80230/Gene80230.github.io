---
title: 开始学习CSS
date: 2019-08-21 18:50:37
tags:
---
### 开始学习CSS（Cascading Style Sheets）
### 引入css的方式
- 内联样式：放在标签内写style属性
```html
<h1 style="text-align:center;">Gene</h1>
```
- style标签引入：把style标签放在head标签中
```html
<style>
    h1{text-align:center;}
</style>
```
- 外部样式： 用link来连接，css属性写入css文件中
```html
<link rel="stylesheet" href="./style.css">
```
### 浮动float
用了float之后会有bug，我们只需要记住，给你浮动元素的父元素加上一个类clearfix，这个类的css属性如下：
```css
.clearfix::after{
    content:'';
    display:block;
    clear:both;
}
```
这样，就能让列表变成横向，从而不产生bug
#### ul消除样式
```css
ul{list-style: none;}
```
#### a消除样式
a标签默认取值为underline（下划线），我们可以让它的值为none，取消下划线

overline（上划线）
line-through（中划线）
```css
a{text-decoration:none;}
```
#### 如何解决hover之后元素会多出像素
我们可以在hover之前就让它存在，并且它是透明的，比如a元素的边框:
```css
.topNavBar>nav>ul li a{
    border:1px solid transparent;  //透明色
}
```
### 布局
#### css布局：横向 ＆ 纵向
如有3个div，两个在上，一个在下，前面两个为横向布局看作一个整体之后，与第三个div成纵向布局。

#### 其他
页面上默认字体大小是16px