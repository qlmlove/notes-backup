---
title: Linux安装nodejs、hexo、以及php
tags: Linux
date: 2017-09-24 09:16:15
---

## 安装nodeJS

方式一

```
sudo apt-get install nodejs -y
sudo apt-get install npm -y
```

方式二

`sudo git clone https://github.com/nodejs/node.git`

修改目录权限：

`sudo chmod -R 755 node`

使用 ./configure 创建编译文件，并按照：

```
cd node
sudo ./configure
sudo make
sudo make install
```

查看 node 版本：
 
`node -v`

## 安装hexo

`npm install -g hexo-cli`
