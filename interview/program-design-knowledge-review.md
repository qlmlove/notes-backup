---
title: 程序设计知识总结
tags: [程序设计]
date: 2017-12-18 14:53:27
---

## 练习题

编写一个在线留言本,实现用户的在线留言功能,留言信息存储到数据库,要求设计数据表内容以及使用PHP编码完成.

<font color='red'>**注意:**</font>根据题目要求的功能,先分析应该存储哪些信息,设计好数据表<font color='green'>(***这是很关键的一步,如果编码时才发现设计有问题,会浪费大量时间,基本没有时间改,所以要先设计好***)</font>,然后根据设计好的数据表创建数据表,通常应该使用<font color='red'>**PDO**</font>来连接数据库,最终完成编码,所以一定要熟悉<font color='red'>**PDO**</font>的基本操作.

### 数据表设计

#### 分析表结构

留言板有哪些信息需要存储
    
 - 留言信息:ID,标题,内容,时间,用户名

### 数据表创建语句

留言表message

```SQL
CREATE TABLE message(
    'id' INT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
    'title' VARCHAR(120) NOT NULL DEFAULT '',
    'content' VARCHAR(255) NOT NULL DEFAULT '',
    'create_at' INT NOT NULL DEFAULT '0',
    'username' VARCHAR(32) UNSIGNED NOT NULL DEFAULT '',
    KEY message_username(username)
)ENGINE=InnoDB DEFAULT CHARSET=utf8;

```
### 选择PHP数据库的连接方式
1. <font color='red'>**PDO**</font>
    - 可扩展性好
    - 支持预处理
    - 面向对象

        ```php
        <?php
            try{
                # 操作数据库代码
            }catch(PDOException $e){
                echo $e->getMessage();
            }
        ```
        数据库操作代码
        ```php
        $pdo = new PDO($dsn,$username,$password,$attr);
        $sql = 'SELECT id,title,content FROM message where username = :username;
        $stmt = $pdo->prepare($sql);
        $stmt->execute([':username' => $username]);
        $result = $stmt->fetchALL(PDO::FETCH_ASSOC);
        ```

2. mysqli
    - 只支持MySQL操作
    - 支持预处理
    - 面向对象和过程
    - 效率较高

3. mysql
    - 只支持MySQL数据库
    - 没有预处理的支持
    - 面向过程


### 编码

编码省略

## 无限分类

|id|category_name|pid|[path]|
|:|:|:|:|
|分类id|分类名|父分类id|[可选整体路径]