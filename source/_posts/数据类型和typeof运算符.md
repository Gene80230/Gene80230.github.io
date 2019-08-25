---
title: 数据类型和typeof运算符
date: 2019-08-24 18:32:18
tags:
---
## 数据类型和typeof运算符
### 数据类型
JavaScript 语言的每一个值，都属于某一种数据类型。JavaScript 的数据类型，共有七种。
- 数值（number）：整数和小数（比如1和3.14）
- 字符串（string）：文本（比如Hello World）。
- 布尔值（boolean）：表示真伪的两个特殊值，即true（真）和false（假）
- undefined：表示“未定义”或不存在，即由于目前没有定义，所以此处暂时没有任何值
- null：表示空值，即此处的值为空。
- 对象（object）：各种值组成的集合。
- Symbol (这里不讨论)

**原始类型**
`数值`、`字符串`、`布尔值`这三种类型，合称为原始类型（primitive type）的值，即它们是最基本的数据类型，不能再细分了。

**两个特殊值**
至于`undefined`和`null`，一般将它们看成两个特殊值。

**合成类型**
`对象`则称为合成类型（complex type）的值，因为一个对象往往是多个原始类型的值的合成，可以看作是一个存放各种值的容器。
`对象`是最复杂的数据类型，又可以分成三个子类型。
- 狭义的对象（object）
- 数组（array）
- 函数（function）

### Number
**十进制**
没有前导`0`的数值。
```js
1
1.1
1.2E^2      //科学计数法
```
**二进制**
有前缀`0b`或`0B`的数值。
```js
0B11    //3
```
**八进制**
有前缀`0o`或`0O`的数值，或者有前导0、且只用到0-7的八个阿拉伯数字的数值。
```js
011      //9
```
比如你要存储一个电话号码
如果0开头，很容易会变为我们不想要的结果
![Markdown](http://i1.fuimg.com/644982/b5db73832fcc625d.png)
所以我们推荐用字符串来存储

**十六进制**
有前缀0x或0X的数值。
```js
0x11    //17
```
### String
**一般表现形式：**
```js
'你好'  "你好"
```

**空字符串与空格字符串**
- 空字符串：
![Markdown](http://i1.fuimg.com/644982/b52ed8917069bd19.png)

- 空格字符串：
![Markdown](http://i1.fuimg.com/644982/33769e08a63b7bd2.png)

这两个需要格外注意，空字符串的长度为0。空格字符串的长度为1

**转义**
- 一般转义方法
当我们需要在字符串里面表示单/双引号的时候，我们可以用以下方法：
```js
    var a = " ' "
```
- 当然我们有些时候因为需要有单双引号在同一个字符串中,这个时候用上面的方法会报错
```js
    var a = " ' ""   
```
- 如何表示引号
这个时候我们需要用反斜杠来表示转义
```js
    var a = "\ ' ""   
```
这样就不会报错啦

- 如何表示特殊符号
有时候我们需要一些特殊的符号，如回车、Tab（制表符）、反斜杠（\）
我们可以这样表示：
```js
    var enter = "\ n "   //回车
    var t = " \t "  //Tab 制表符
    var b = " \\ "  //反斜杠
```
- 多行字符串
![Markdown](http://i1.fuimg.com/644982/0dad00a2b4d4ac09.png)
这样会报错，我们可以用反斜杠来处理它:
![Markdown](http://i1.fuimg.com/644982/4fa263a139178f5c.png)
但一般不建议这样做，我们更推荐这样：
![Markdown](http://i1.fuimg.com/644982/30eca457fd489282.png)
原因是当斜杠后面有空格时也是会报错的
![Markdown](http://i1.fuimg.com/644982/a9121d3ca2b207b6.png)
ES6的新语法可以用`\``  也就是键盘1隔壁那个反引号，可以直接用来写多行字符串

### Boolean
`true`表示真

`false`表示假

最常见的用法就是用来判断:
```js
if(a){  //如果a是真的就执行下面的代码，是假的就不执行
    ...
}
```

这里还要再说下 &&（与运算）、||（或运算）
这两个逻辑运算符的判断方式：
![Markdown](http://i1.fuimg.com/644982/f77d532dd1873030.png)

### null
这是 空 的意思，一般出现有一个对象(object)，暂时不需要赋值你可以把它赋值为null
```js
var obj = null
```
### undefined
这是 未定义 的意思，一般出现在有一个非对象，暂时不需要赋值你可以把它赋值为undefined
```js
var n   //undefined
```
### 对象（Object）
上面的几种都是基本类型（简单类型），而对象是复杂类型，由基本类型组成。
```js
var name = 'gene'
var age = 17
var gender = 'male'

//我们可以把它们写在一个对象里面
var person = {
name : 'gene',   //key引号可有可无
'age' : 17,
'children' : {name : 'xxx', age : 2,}    //对象中还可加入其它对象
'gender' : 'male',     //最后一个key后面的逗号如果在ES3（IE7以下）是不可以的
}

person['name']  //要用的时候这样引用就可以了
person.name  //等同于上面
```
**如何读取**
![Markdown](http://i1.fuimg.com/644982/2ef8913ccdcbf078.png)

当你不用引号时要遵循变量的命名规则，上图中对象`obj`的key是数字开头，这样会导致报错，如果你想用数字开头命名key，这里推荐你给它加上引号。

**in运算符 & 删除key的正确方式：**
- `in`运算符
`in`可以让你知道一个变量在不在某个对象中，在为true，不在就为false
![Markdown](http://i1.fuimg.com/644982/680ab47d2f85e929.png)
- 删除key（`delete`命令）
上面第一段删除key的操作为`true`，表示已经成功让key在对象中被删除。
后面的演示只是让key的值等于undefined而已，在访问用`in`时还等于`true`，可以看到并不是删除。

**for...in循环**
`for...in`循环用来遍历一个对象的全部属性。
下面是一个使用`for...in`循环，提取对象属性名的例子
![Markdown](http://i1.fuimg.com/644982/0c594d83c6612e63.png)

注意：
- 它遍历的是对象所有可遍历（enumerable）的属性，会跳过不可遍历的属性。它
- 不仅遍历对象自身的属性，还遍历继承的属性。

### typeof运算符
`typeof`运算符可以返回一个值的数据类型。
JavaScript 有三种方法，可以确定一个值到底是什么类型。
- `typeof`运算符
- `instanceof`运算符
- `Object.prototype.toString`方法

![Markdown](http://i1.fuimg.com/644982/2e235fcd902b5397.png)
注意：
七种数据类型中，只有`null`返回的是`object`
![Markdown](http://i1.fuimg.com/644982/03f91cd8d8e6aa3b.png)

还有一个在七种类型之外的函数，返回的是`function`，其余都是返回对应的类型。
![Markdown](http://i1.fuimg.com/644982/ca5b9c208c719530.png)

而数组就正常多了，返回的是'object'
![Markdown](http://i1.fuimg.com/644982/cf0e4bd631e9003e.png)