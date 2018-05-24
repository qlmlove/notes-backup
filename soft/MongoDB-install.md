---
title: MongoDB安装
tags: [MongoDB]
date: 2017-12-20 00:54:58
---

## 将MangoDB安装为window服务
```bash
mongod --logpath "C:\data\mongo\log\mongod.log" --logappend --dbpath "C:\data\mongo\db" --directoryperdb --serviceName "MongoDB" --serviceDisplayName "MongoDB" --install
 # 该命令行指定了日志文件：C:\data\mongo\log\mongod.log，日志是以追加的方式输出的；

# 数据文件目录：C:\data\mongo\db，并且参数--directoryperdb说明每个DB都会新建一个目录；
# Windows服务的名称：MongoDB；
# 最后是安装参数：--install，与之相对的是--remove
# 启动MongoDB：
net start MongoDB
# 停止MongoDB：
net stop MongoDB
```

## 安装PHP扩展

1. 命令方式(我没装成功)

    ```bash
    $ pecl install mongodb
    $ echo "extension=mongodb.so" >> `php --ini | grep "Loaded Configuration" | sed -e "s|.*:\s*||"`
    ```

2. 手动去下载

    [http://pecl.php.net/package/mongodb/](http://pecl.php.net/package/mongodb/)下载zip,然后将dll文件解压到PHP的ext目录下

 - 修改php.ini 添加 `extension=php_mongodb.dll`

3. 重启服务器