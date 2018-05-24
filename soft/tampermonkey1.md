---
title: 廖雪峰网站滚动目录油猴插件
date: 2017-09-05 18:40:54
tags: [TamperMonkey,JavaScript]
---
在廖雪峰的网站学习Python3的时候，文章翻到下边之后左侧的目录就看不见了，而且下边的上一章下一章链接又被好大的几块广告挡着，所以写了这个插件让左侧的目录中的当前项持续处于屏幕中央，方便点击，大神请自觉无视
```javascript
// ==UserScript==
// @name         廖雪峰网站滚动目录
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  让廖雪峰网站的目录相对屏幕固定
// @author       柠娇黎
// @match        https://www.liaoxuefeng.com/wiki/*
// @grant        none
// ==/UserScript==
// @require  https://cdn.bootcss.com/jquery/3.2.1/jquery.js

(function() {
    'use strict';
    var number_lm = $("ul.uk-nav-side").children("li.uk-active").index();
    number_lm = 500-number_lm*30+"px";
    $("div.x-sidebar-left").css({"position":"fixed","top":number_lm});
})();
```