---
title: yii2学习笔记
tags: [PHP,Yii2]
---

## 1.yii框架的安装
### 1.1 Composer安装：

    curl -sS http://install.phpcomposer.com/installer | php
### 1.2 安装插件

    php composer.phar global require "fxp/composer-asset-plugin:~1.1.1"

### 1.3 安装yii2.0.7框架

    php composer.phar create-project --prefer-dist yiisoft/yii2-app-basic basic 2.0.7
