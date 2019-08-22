---
title: 继续学习CSS
date: 2019-08-22 21:15:07
tags:
---
## 继续学习CSS

### 高度是由什么决定的
div高度 由其内部文档流元素的 `高度总和` 决定
>文档流：文档内元素的流动方向
>1. 内联元素由左往右流动，汉字会在遇到阻碍的时候换行，单词则不会换行，且会保持一个整体，如果要打断我们可以用css属性 work-break:break-all; 
>2. 块级元素由上到下流动，每个块级元素另起一行。
- 内联元素
    一般由最高的那个元素的高度决定
- 块级元素
    由它内部文档流元素的总和决定

### 解决设置width：100%后元素溢出的问题
当你给某个元素宽度100%之后，如有padding之类的属性，这个元素可能会超出，这时你应该给它在外层再嵌套一个div，之后只需要给这个div加入相同的属性就可以了

### 如何脱离文档流？
- float     浮动
- postion:fixed;  相对于窗口定位
- postion：absolute    相对于加了`position：relative`的父元素定位

### 如何在div上面给一层遮罩？
应先给div内部一个元素，此元素的bgcolor设置为有透明度的rgba即可

### 图片的设置方式
```css
background-position:center center;  //居中
background-size:cover;      //自适应 全覆盖
```
### animation 
animation属性用来指定一组或多组动画，每组之间用逗号相隔。
该例中<p> 元素由浏览器窗口右边滑至左边
```css
p {
  animation-duration: 3s;
  animation-name: slidein;}

@keyframes slidein {
  from {
    margin-left: 100%;
    width: 300%; 
  }

  to {
    margin-left: 0%;
    width: 100%;
  }}
```
### 过渡动画
```css
transition:box-shadow 0.3s;
```
### 解决加了display:inline-block之后元素向下移的问题
加了 `display:inline-block`之后一定要加`vertical-align:top`

### 状态机
```css
.portfolio .bar.state-1 .bar-inner{
    width:28%;
    margin-left:0;
}
.portfolio .bar.state-2 .bar-inner{
    width:28%;
    margin-left:96px;
}
.portfolio .bar.state-3 .bar-inner{
    width:22%;
    margin-left:186px;
}
```
```js
portfolio1.onclick = function(){
    portfolioBar.className="bar state-1"
}
portfolio2.onclick = function(){
    portfolioBar.className="bar state-2"
}
portfolio3.onclick = function(){
    portfolioBar.className="bar state-3"
}
```

### 其他
- 当你写了width，height之后，我们就需要line-height跟height一样高来自动居中。但这只在低像素值的时候有效。

- 不加width height ，我们可以加padding，这样不容易有bug。
- CSS position 有哪些取值？
sticky、absolute、fixed、relative、static

- 字体默认的 line height 由字体设计师决定
- CSS 中 width 的默认值是多少？
    auto

- content-box 与 border-box 的区别是
    1. content-box 的 width 不包括 padding 和 border 
    2. border-box 的 width 包括 padding 和 border

- 关于文档流（Normal Flow）
    1. 文档流代表元素在文档中的「流动」方向 
    2. float:left、position:fixed、position:absolute 都能使元素脱离文档流

- 关于 display: inline 元素，描述正确的是
    1. 给 display: inline 元素设置宽高是无效的
    2. 给 display: inline 元素设置 margin-top margin-top 是无效的

