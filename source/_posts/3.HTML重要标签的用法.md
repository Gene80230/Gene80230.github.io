---
title: HTML重要标签的用法
date: 2019-08-20 18:50:07
tags:
---
在[上一节](https://gene80230.github.io/2019/08/18/HTML%E5%B8%B8%E7%94%A8%E6%A0%87%E7%AD%BE%E4%BB%8B%E7%BB%8D/)中我们已经介绍了HTML的常用标签。接下来我们就来看下一些标签的用法。

### img 标签 
在页面中显示图片，接下来我们来看看它的属性
**src 属性**
```html
<img src="图片的路径" />
```
实际上不是将一张图片嵌入到网页中，而是通知服务器发起一个get请求，请求服务器找到图片并且加载。

**height 属性 ＆ width 属性**
`height`属性是高度，`width`是宽度，单位是像素和百分比。

**alt 属性**
alt属性在图片无法加载裂开时占住图片位置的文字。

**title**
title属性会在鼠标悬停时提示文字。

### iframne 标签

1. iframe标签可以在所在页面中的位置再嵌套一个窗口，但必须要有src属性，src属性指明将要嵌入页面的url。以此来达到交互效果。
2. 当我们我们需要给iframe的提供一个name属性 让a标签的target属性的值与之对应，就可以在iframe中打开指定的网页了。如下：
```JS
<iframe src="#" name="xxx" frameborder="0"></iframe>
<a href="http://baidu.com" target="xxx">度娘</a>
<a href="http://qq.com" target="xxx">QQ</a>
```
### a 标签
我们都知道a标签是可以在网页中实现跳转的，但这只是它其中的一个功能而已，它还有另外一个功能，我们现在指定一个a标签让它跳转到index2页面，它肯定会按照我们说的跳转到index2页面。
```html
<a href="./index2.html">点我</a>
```
我们来看下请求头，然后发现，它居然发起了一个get请求。
![a.png](https://i.loli.net/2019/08/20/iynWxaFSeV9jRuf.png)
所以我们现在要知道的是，它不止会跳转，跳转的时候还会发起请求。接下来我们来看看它的属性

**target 属性** 
主要有四个值，如下：
`_blank`  在空页面打开
`_self`   在当前页面（自身）中打开
`_parent`     在上一级页面中打开
`_top`    在最顶级（祖先）页面中打开

**download 属性** 
用于下载
```html
<a href="#" download>Download</a>
```
如果HTTP响应的内容为：
1. Content-type : application/octet-stream  
浏览器会以下载的形式去接收这个请求

2. Content-type : text/html   这种格式，我们要实现下载就需要在a标签中写入download属性来下载这个文件

**href 属性**
指定地址
1. href="http://qq.com"  http协议写法  可以跳转到QQ的官网  推荐使用
2. href="//qq.com" 无协议写法   当前文件什么协议a标签就会以什么协议去跳转
3. href="?name=Gene"   浏览器会自动补全并发起一个get请求   #不发起请求
4. 如果不写href属性则a标签会变成一个span  没有了颜色和下划线
5. 如需要点击a不做任何动作可以用下面伪协议的第二种写法

**伪协议**
这是一个历史遗留问题，一般推荐使用下面`2`的写法
1. `href="javascript: alert(1);"`  //会弹出对话框
2. `href="javascript: ;"`    //点击之后什么都不做

### form 标签
form 标签也是可以跳转页面的，会HTTP POST请求，不过要注意file协议不支持。
下面我们来看看它的属性

**action 属性**
1. action 属性的作用是用来指定请求路径
2. 如果form表单中没有提交按钮，你就无法提交form表单

语法:
```html
<form action="users">
    <input type="submit" value="提交">
</form>
```
当然啦，如果我们没有写method的话，form默认是发起get请求的，所以我们要在上面的基础上加上method方法为post，像这样：
```html
<form action="users" method="post">
    <input type="submit" value="提交">
</form>
```
我们就可以发起post请求了。
![Image.png](https://i.loli.net/2019/08/20/YrIbOLMg8uH6eSf.png)

我们还可以再在forn表单中添加进提交的内容，如用户名和密码：
```html
<form action="users" method="post">
    <input type="text" name="xxx">
    <input type="password" name="xxx">
    <input type="submit" value="提交">
</form>
```
这样我们可以在form data中看到我们提交的内容
![Image _2_.png](https://i.loli.net/2019/08/20/p9SfBxQRXqGucoO.png)
假如我们用中文作为密码呢？
我们会看到这样的Form Data内容
![Image _3_.png](https://i.loli.net/2019/08/20/XPKl9wzrgStZ6Rv.png)
但是我们千万不能被骗了，当我们点击view source之后：
![Image _4_.png](https://i.loli.net/2019/08/20/FDMxrSG6LhbYqAc.png)
这个格式因为http请求是由响应的第二部分的Content-Type决定的，我们可以看看上图的Content-Type类型，这就是它决定的第四部分内容（Form Data）的呈现方式。

**但如果我们是get的时候写了密码呢？**
答案是 它会让密码出现在查询参数那里，不会放在第四部分。
**关于submit ＆ button**
`submit` 是用来提交数据的
如果一个form里面只有一个`button`按钮（没有type类型），那么它会自动升级为提交按钮，在页面中它会像这样：
```html
<button>button</button>
```

### input 标签
接下来我们来看下不同的type类型
**button**  就是一个按钮

**checkbox**  多选框
这是一个选框，语法如下：
```html
<input type="checkbox" id="love"><label for="love"> 爱我</label>
```
当你想做点击选框后面的文字就会选中选框的效果，你可以把选框后面的文字放入label标签，让for属性的值和id的值对应就可以了。
不过我们可以把它优化下，如：
```html
<label><input type="checkbox">爱我</label>
```
像这样也是可以得到同样的效果的，当然你也可以把text，password类型的input这样用label包起来，都可以达到选中文字就选中选框的效果。
```html
<label><input type="checkbox" name="fruit" value="apper">苹果</label>
<label><input type="checkbox" name="fruit" value="banana">香蕉</label>
<input type="submit" value="提交">
```
像上面这样就是一个常用的多选框的写法，提交之后，查询参数那里会出现你选择的数据,同组需要name值相同
![Markdown](http://i1.fuimg.com/644982/4fb2603e1e3cc040.png)
![Markdown](http://i1.fuimg.com/644982/2b01eeccdc3e09f6.png)

**radio**  单选框
```html
<label><input type="radio" value="yes">yes</label>
<label><input type="radio" value="no">no</label>
```
上面是一个普通的单选框写法，但是这样会两个都能被选中，如何只能选择一个呢？
我们需要给每个单选框加上同样的name值，这样就只能选择一个了。
```html
<label><input name="love" type="radio" value="yes">yes</label>
<label><input name="love" type="radio" value="no">no</label>
```

**select**  下拉列表
```html
<select name="group" multiple>
    <option value="">-</option>
    <option value="1">第一组</option>
    <option value="2">第二组</option>
    <option value="3" disabled>第三组</option>
    <option value="4" selected>第四组</option>
</select>
```
给select里面的值是multiple，表示可以多选

给option里面的值是disabled，表示不可以被选中，如下：
![Markdown](http://i1.fuimg.com/644982/ff6817749d6af7ad.png)

给option里面的值是selected，表示默认被选中，如下：
![Markdown](http://i1.fuimg.com/644982/5a6c97a1844bc378.png)

**textarea**
```html
<textarea name="love" style="resize:none; width:330px; height:100px;" cols="30" rows="10"></textarea>
```
一般我们写多行文本框需要给它一个name，方便我们提交的时候看查询参数。
我们可以通过css的宽高来给它加样式，`cols`、`rows`不是很准确。
我们还可以让它的`resize:none;`这样它就不可以被拉动了

### table 标签 
常用表格写法:
加了border之后，边框会重合，我们可以用css属性`border-collapse: collapse;`来清除它
![Markdown](http://i1.fuimg.com/644982/491680d10bca07bd.png)

**其他**
`<a href="#">link</a> `标签被点击后会发生什么？ 
页面锚点变成 #，页面滚动到顶部 
