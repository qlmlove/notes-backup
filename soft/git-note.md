---
title: git笔记
tags: [Git]
date: 2017-12-04 23:46:36
---
## 创建版本库

```bash
git init # 初始化仓库
```
## 添加文件到版本库
```bash
git add a.txt b.rar # 添加多个文件
# 或者
git add. # 添加所有文件
```

## 添加commit信息

```bash
git commit -m 'first commit'
```

## 链接远程仓库

```bash
git remote add origin https://github.com/username/ProjectName.git
```

## 推送到远程仓库

```bash
git push -u origin master
```

##生成公钥

打开命令行终端输入`ssh-keygen -t rsa -C "your_email@example.com"`( 你的邮箱)，连续点击`Enter`键即可。

    ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
    # Creates a new ssh key, using the provided email as a label
    # Generating public/private rsa key pair.
    Enter file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]  // 推荐使用默认地址
    Enter passphrase (empty for no passphrase):   //此处点击 Enter 键即可，也可以填写密码，填写密码后每次使用 SSH 方式推送代码时都会要求输入密码，由于这个 Key 也不是用于军事目的，所以也无需设置密码。

成功之后显示如下信息：

    Your identification has been saved in /Users/you/.ssh/id_rsa.
    # Your public key has been saved in /Users/you/.ssh/id_rsa.pub.
    # The key fingerprint is:
    # 01:0f:f4:3b:ca:85:d6:17:a1:7d:f0:68:9d:f0:a2:db your_email@example.com