---
title: Linux基础知识总结
tags: [Linux]
date: 2017-12-18 14:52:00
---

## Linux常用命令

### 系统安全

- sudo
- su
- chmod
- setfacl

### 进程管理

- w
- top
- ps
- kill
- pkill
- pstree
- killall

### 用户管理

- id
- usermod
- useradd
- groupadd
- userdel

### 文件系统

- mount
- umount
- fsck
- df
- du

### 系统关机和重启

- shutdown
- reboot

### 网络应用

- curl
- telent
- mail
- elinks

### 网络测试

- ping
- netstat
- host

### 网络配置

- hostname
- ifconfig

### 常用工具

- ssh
- screen
- clear
- who
- date

### 软件包管理

- yum
- rpm
- apt-get

### 文件查找比较

- locate
- find

### 文件内容查看

- head
- tail
- less
- more

### 文件处理

- touch
- unlink
- rename
- ln
- cat

### 目录操作

- cd
- mv
- rm
- pwd
- tree
- cp
- ls

### 文件权限属性

- setfacl
- chmod
- chown
- chgrp

### 压缩解压

- tar

- bzip2/bunzip2

- gzip/gunzip

- zip/unzip

### 文件传输

- ftp
- scp


## 系统定时任务

### crontab命令

指定时间段重复执行

```bash
crontab -e # 创建定时任务
* * * * * 命令(分 时 日 月 周)
```

### at命令

指定时间点单次执行

```bash
at 2:00 tomorrow # 设定时间点
at>/home/lm/do_job # 执行的任务
at>Ctrl + D # 退出at
```
## vi/vim编辑器

### 模式

1. 一般模式：复制、粘贴、删除
2. 编辑模式
3. 命令行模式

#### 切换编辑模式：

i、I、o、O、a、A、r、R

#### 切换到命令行模式： 

:  /  ?

### 移动光标

ctrl+f 、ctrl+b 、 0或者功能键Home 、 $或者功能键End 、 G 、 gg 、 N+enter

### 查找和替换

```bash
/word
?word
:n1,n2s/word1/word2/g
:1.$s/word1/word2/g
:1,$s/word1/word2/gc
```

### 删除、复制和粘贴

```bash
x,X
dd
ndd
yy
nyy
p
P
ctrl+r
.
```

### 保存和退出
```bash
w
q
wq
```

### 视图模式(vim)

```bash
v
V
ctrl+v
y
d
```

### 配置

```bash
:setnu #显示行号
:setnonu # 不显示行号
```

## shell基础

### 脚本执行方式

1. 赋予权限,直接执行,例:`chmod +x test.sh;./test.sh`
2. 调用解释器使得脚本执行,例:`bash csh ash bsh ksh`等
3. 使用source命令,例:`source test.sh`

### 编写基础

- 开头用#!指定脚本解释器,例:`#!/bin/sh`
- 编写具体功能
