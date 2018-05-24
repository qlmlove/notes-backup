---
title: Linux使用笔记
tags: Linux
date: 2016-05-17 15:25:22
---


1.  `sudo gnome-open XXX`以ROOT权限打开XXX文件夹
2.  找出那些引起“404 无法找到”错误的PPA命令`sudo apt-get update | grep Failed`

3.  移除PPA仓库命令 `sudo add-apt-repository --remove ppa:finalterm/daily` （PPA：修改后边的内容）
4.  安装虚拟光驱`sudo apt-get install acetoneiso`

5.  打命令：`nm-connection-editor` 添加DSL就行了

6.  在Linux或者mac下使用dd来做，windows下请自行搜索dd的windows版以及用法，命令`dd if=path/fedora.iso of=/dev/sdX`

    #### 注意问题

    1.  if指向的是iso镜像 of指向的是写入目标，不要弄反了，反了就把磁盘做成iso了
    2.  of的指向目标是整个磁盘，比如是/dev/sde,而不是类似/dev/sde1这样的某个磁盘分区

#### 住处附近的wifi账号

shuichang密码
bjhysyjtgs

### kali2.0声音问题

`systemctl --user enable pulseaudio`
