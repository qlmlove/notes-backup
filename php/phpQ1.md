---
title: php比较字符串长度的另类解法
tags: []
date: 2018-04-11 16:25:34
---
PHP中遇到的一个问题

<!--more-->
判断字符串长度是否>5可以采用如下方式

## 代码
```php
$foo = '12345';

echo $foo{5};
if (!isset($foo{5})) { 
	echo "失败:字符长度不足";
} else {
	echo '成功';
}
```
<iframe src="https://tool.lu/coderunner/embed/4um.html" width="650" height="550" frameborder="0"></iframe>