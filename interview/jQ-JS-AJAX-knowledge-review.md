---
title: jQ_JS_AJAX知识总结
tags: [jQuery,JavaScript,AJAX]
date: 2017-12-18 14:49:59
---

## JavaScript基本语法

### 变量的定义

- 变量必须以字母/下划线/$开头
- 对大小写敏感
- 使用var关键字来声明变量
- 可以在一条语句中声明许多变量,例:`var a=1,b=2,c=3`
- 未使用值来声明的变量,值为`undefined`
- 如果重新声明JavaScript变量,但是没有再次赋值,该变量原来的赋值不会丢失
   
    ```javascript
    var a =1;
    var a;// 此处a依然是1
    ```

### 数据类型

字符串、数字、布尔、对象、Null、Undefined

JavaScript中变量均为对象,当声明一个变量的同时,就创建了一个新的对象

### 创建对象

1. 方法一:
```javascript
new Object()
```

2. 方法二
使用对象构造器

3. 使用JSON对象:{}

### 函数

1. 定义方法
2. 无默认值
3. 函数内部声明的变量(使用var)是局部变量
4. 在函数外声明的变量是全局变量,所有脚本和函数都可以访问它

### 运算符

`+`用来拼接字符串

### 流程控制

`else if`中间必须有空格(PHP中可以写空格或者不写)

## JavaScript内置对象

### Number

三种定义方式

1. `var pi=3.14;`
2. `var myNum = new Number(value);`
3. `var  myNum = Number(value);`

### String

四种定义方式(其中1、2没什么区别):

1. `var str = '字符串';`
2. `var str = "字符串";`
3. `var str = new String(s);`
4. `var str = String(s);`

方法和属性:

- length()

### Boolean

三种定义方式:

1. `var bol = true;`
2. `var bol = new Boolean(value);`
3. `var bol = Boolean(value);`

方法和属性:

### Array

三种定义方式:

1. `var arr = new Array();`
2. `var arr = new Array(size);`size指定数组长度
3. `var arr = new Array(e1,e2,e3,...,en)`放入n个元素

方法和属性:

**<font color='red'>注:没有关联数组,只有索引数组</font>**

### Date

定义方式;

`var date =new Date();`

方法和属性:

### Math

定义方式:

1. `var my_pi = Math.PI;`不用new就可以使用
2. `var sqrt_value = Math.sqrt(15);`求15的平方根

方法和属性:

### RegExp(正则表达式)

定义方式:

1. /pattern/attributes

><font color='red'>注:不用加引号,否则就变成字符串了</font>

2. new RegExp(pattern,attrobutes);

方法和属性:


## Window对象

Window
Navigator
Screen
History
Loction
## DOM对象

Document
Element
Attr
Event
## jQuery基础知识

### jQuery选择器

1. 基本选择器
2. 层次选择器
3. 过滤选择器
4. 可见性过滤选择器
5. 属性过滤选择器
6. 子元素过滤选择器
7. 表单对象属性过滤选择器

### jQuery事件

`$("button").click(function(){//执行的操作})`

### jQuery效果

显示,隐藏等

`$("p").show()`

### DOM操作

1. **属性**
2. **值**
3. 节点
4. **CSS**
5. 尺寸


## 练习1

1. JavaScript中为id是test的元素设置样式为good

```javascript
document.getElementById('test').className = 'good';
```
2. 使用jQuery事件在页面元素加载完成之后,动态绑定click事件到btnOK元素

```javascript
$(function(){
    $(".btnOK").click(function(){
        //要执行的代码
    })
});
```

## AJAX基础知识 
### AJAX基本工作原理

#### AJAX基本概念
Asynchronous(异步) JavaScript and XML
通过在后天与服务器进行少量数据交换,AJAX可以使网页实现异步更新

#### AJAX工作原理
XMLHttpRequest对象是AJAX基础
XMLHttpRequest对象用于在后台与服务器交换数据

#### XMLHttpRequest对象请求

```javascript
open(method,url,async) //method:get/post,async:是否异步传输   
send(string)
```

#### XMLHttpRequest对象响应

两种响应方式:

1. responseText
2. responseXML

方法和属性:

1. onreadystatechange
2. readyState:0(请求未初始化),1(服务器连接已建立),2(请求已接收),3(请求处理中),4(请求已完成,且响应已就绪)
3. status:200,400

### jQuery的AJAX操作

#### 常用方法
$(ele).load()
$.ajax()
$.get()
$.post()
$.getJSON()
$.getScript()