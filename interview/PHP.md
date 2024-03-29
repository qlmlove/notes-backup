---
title: PHP试题
tags: PHP
---

一、PHP基础：
-------------

### 1. WEB开发中数据提交方式有几种？有什么区别？百度使用哪种方式？

Get与post两种方式

1. 区别：

        1. Get从服务器获取数据，post向服务器传送数据
        2. Get传值在url中可见，post在url中不可见
        3. Get传值一般在2KB以内，post传值大小可以在php.ini中进行设置
        4. get安全性非低，post安全性较高，执行效率却比Post高


2. 建议：

        1. get式安全性较Post式要差些包含机密信息建议用Post数据提交式；
        2. 做数据查询建议用Get式；做数据添加、修改或删除建议用Post方式；

    百度使用的get方式，因为可以从它的URL中看出


### 2. 在程序的开发中，如何提高程序的运行效率？

    1. 优化SQL语句，查询语句中尽量不使用select *，用哪个字段查哪个字段；
    少用子查询可用表连接代替；
    少用模糊查询；
    2. 数据表中创建索引；
    3. 对程序中经常用到的数据生成缓存；

### 3. 现在编程中经常采取MVC三层结构，请问MVC分别指哪三层，有什么优点？

MVC三层分别指：

> 业务模型、视图、控制器，由控制器层调用模型处理数据，然后将数据映射到视图层进行显示，优点是：
>
>     ①可以实现代码的重用性，避免产生代码冗余；
>     ②M和V的实现代码分离，从而使同一个程序可以使用不同的表现形式

### 4.对json数据格式的理解？

> JSON(JavaScript Object Notation)是一种轻量级的数据交换格式，json数据格式固定，可以被多种语言用作数据的传递。
>
> PHP中处理json格式的函数为`json_decode(string $json [, bool $assoc])`，接收一个 JSON格式的字符串并且把它转换为PHP变量，参数json表示待解码的json string格式的字符串。当assoc参数为TRUE时，将返回array而非object；
>
> Json\_encode：将PHP变量转换成json格式

### 5.Print、echo、print\_r有什么区别？

> ① echo和print都可以做输出，不同的是，echo不是函数，没有返回值，而print是一个函数有返回值，所以相对而言如果只是输出echo会更快，而print\_r通常用于打印变量的相关信息，通常在调试中使用。
>
> ② print 是打印字符串
>
> ③ print\_r 则是打印复合类型 如数组 对象

### 6.SESSION与COOKIE的区别？

> ①存储位置：session存储于服务器，cookie存储于浏览器
>
> ②安全性：session安全性比cookie高
>
> ③session为‘会话服务’，在使用时需要开启服务，cookie不需要开启，可以直接用

### 7.PHP处理数组的常用函数？（重点看函数的‘参数’和‘返回值’）

> ①array()创建数组；
> ②count()返回数组中元素的数目；
> ③array\_push()将一个或多个元素插入数组的末尾（入栈）；
> ④array\_column()返回输入数组中某个单一列的值；
> ⑤array\_combine()通过合并两个数组来创建一个新数组；
> ⑥array\_reverse()以相反的顺序返回数组；
> ⑦array\_unique()删除数组中的重复值；
> ⑧in\_array()检查数组中是否存在指定的值；

### 8.PHP处理字符串的常用函数？（重点看函数的‘参数’和‘返回值’）

> ①trim()移除字符串两侧的空白字符和其他字符；
> ②substr\_replace()把字符串的一部分替换为另一个字符串；
> ③substr\_count()计算子串在字符串中出现的次数；
> ④substr()返回字符串的一部分；
> ⑤strtolower()把字符串转换为小写字母；
> ⑥strtoupper()把字符串转换为大写字母；
> ⑦strtr()转换字符串中特定的字符；
> ⑧strrchr()查找字符串在另一个字符串中最后一次出现；
> ⑨strstr()查找字符串在另一字符串中的第一次出现（对大小写敏感）；
> ⑩strrev()反转字符串；
> ⑪strlen()返回字符串的长度；
> ⑫str\_replace()替换字符串中的一些字符（对大小写敏感）；
> ⑬print()输出一个或多个字符串；
> ⑭explode()把字符串打散为数组；
> ⑮is\_string()检测变量是否是字符串；
> ⑯strip\_tags()从一个字符串中去除HTML标签；
> ⑰mb\_substr()用来截中文与英文的函数

### 9. PHP处理时间的常用函数？（重点看函数的‘参数’和‘返回值’）

> date\_default\_timezone\_get()返回默认时区。
>
> date\_default\_timezone\_set()设置默认时区。
>
> date()格式化本地时间／日期。
>
> getdate()返回日期／时间信息。
>
> gettimeofday()返回当前时间信息。
>
> microtime()返回当前时间的微秒数。
>
> mktime()返回一个日期的 Unix时间戳。
>
> strtotime()将任何英文文本的日期或时间描述解析为 Unix时间戳。
>
> time()返回当前时间的 Unix时间戳。

### 10.PHP操作文件的常用函数？（重点看函数的‘参数’和‘返回值’）

> ①打开文件；
> ②删除文件；
> ③读取文件；
> ④写入文件；
> ⑤修改文件；
> ⑥关闭文件；
> ⑦创建文件

### 11.PHP操作目录（文件夹）的常用函数？（重点看函数的‘参数’和‘返回值’）

> ①打开目录；
> ②删除目录；
> ③读取目录；
> ④创建目录；
> ⑤修改目录；
> ⑥关闭目录

二、数据库
----------

### 1.SQL语言包括哪几部分？每部分都有哪些操作关键字？

> SQL语言包括数据定义(DDL)、数据操纵(DML),数据控制(DCL)和数据查询（DQL）四个部分。
>
> 数据定义：Create Table,Alter Table,Drop Table, Craete/Drop Index等
>
> 数据操纵：Select ,insert,update,delete,
>
> 数据控制：grant,revoke
>
> 数据查询：select

### 2.完整性约束包括哪些？

> 数据完整性(Data Integrity)是指数据的精确(Accuracy)和可靠性(Reliability)。
>
> 分为以下四类：
>
> > 1) 实体完整性：规定表的每一行在表中是惟一的实体。
> >
> > 2) 域完整性：是指表中的列必须满足某种特定的数据类型约束，其中约束又包括取值范围、精度等规定。
> >
> > 3) 参照完整性：是指两个表的主关键字和外关键字的数据应一致，保证了表之间的数据的一致性，防止了数据丢失或无意义的数据在数据库中扩散。
> >
> > 4) 用户定义的完整性：不同的关系数据库系统根据其应用环境的不同，往往还需要一些特殊的约束条件。用户定义的完整性即是针对某个特定关系数据库的约束条件，它反映某一具体应用必须满足的语义要求。

> 与表有关的约束：包括列约束(NOT NULL（非空约束）)和表约束(PRIMARY KEY、foreign key、check、UNIQUE) 。

### 3.什么是事务？及其特性？

> 事务：是一系列的数据库操作，是数据库应用的基本逻辑单位。

> 事务特性：

> > （1）原子性：即不可分割性，事务要么全部被执行，要么就全部不被执行。

> > （2）一致性或可串性。事务的执行使得数据库从一种正确状态转换成另一种正确状态

> > （3）隔离性。在事务正确提交之前，不允许把该事务对数据的任何改变提供给任何其他事务，

> > （4） 持久性。事务正确提交后，其结果将永久保存在数据库中，即使在事务提交后有了其他故障，事务的处理结果也会得到保存。

> 或者这样理解：

> 事务就是被绑定在一起作为一个逻辑工作单元的SQL语句分组，如果任何一个语句操作失败那么整个操作就被失败，以后操作就会回滚到操作前状态，或者是上有个节点。为了确保要么执行，要么不执行，就可以使用事务。要将有组语句作为事务考虑，就需要通过ACID测试，即原子性，一致性，隔离性和持久性。

### 4.什么是锁？

> 数据库是一个多用户使用的共享资源。当多个用户并发地存取数据时，在数据库中就会产生多个事务同时存取同一数据的情况。若对并发操作不加控制就可能会读取和存储不正确的数据，破坏数据库的一致性。

> 加锁是实现数据库并发控制的一个非常重要的技术。当事务在对某个数据对象进行操作前，先向系统发出请求，对其加锁。加锁后事务就对该数据对象有了一定的控制，在该事务释放锁之前，其他的事务不能对此数据对象进行更新操作。

> 基本锁类型：锁包括行级锁和表级锁

### 5.什么叫视图？游标是什么？

> 视图是一种虚拟的表，具有和物理表相同的功能。可以对视图进行增，改，查，操作，视图通常是有一个表或者多个表的行或列的子集。对视图的修改不影响基本表。它使得我们获取数据更容易，相比多表查询。

> 游标：是对查询出来的结果集作为一个单元来有效的处理。游标可以定在该单元中的特定行，从结果集的当前行检索一行或多行。可以对结果集当前行做修改。一般不使用游标，但是需要逐条处理数据的时候，游标显得十分重要。

### 6.什么是存储过程？用什么来调用？

> 存储过程是一个预编译的SQL语句，优点是允许模块化的设计，就是说只需创建一次，以后在该程序中就可以调用多次。如果某次操作需要执行多次SQL，使用存储过程比单纯SQL语句执行要快。可以用一个命令对象来调用存储过程。

### 7.索引的作用？和它的优点缺点是什么？

> 索引就一种特殊的查询表，数据库的搜索引擎可以利用它加速对数据的检索。它很类似与现实生活中书的目录，不需要查询整本书内容就可以找到想要的数据。索引可以是唯一的，创建索引允许指定单个列或者是多个列。缺点是它减慢了数据录入的速度，同时也增加了数据库的尺寸大小。

### 8.如何通俗地理解三个范式？

> 第一范式：1NF是对属性的原子性约束，要求属性具有原子性，不可再分解；
> 第二范式：2NF是对记录的惟一性约束，要求记录有惟一标识，即实体的惟一性；
> 第三范式：3NF是对字段冗余性的约束，即任何字段不能由其他字段派生出来，它要求字段没有冗余。。

### 9.什么是基本表？什么是视图？

> 基本表是本身独立存在的表，在 SQL 中一个关系就对应一个表。 视图是从一个或几个基本表导出的表。视图本身不独立存储在数据库中，是一个虚表

### 10.试述视图的优点？

> (1) 视图能够简化用户的操作
>
> (2) 视图使用户能以多种角度看待同一数据；
>
> (3) 视图为数据库提供了一定程度的逻辑独立性；
>
> (4) 视图能够对机密数据提供安全保护。

### 11.NULL是什么意思

> NULL这个值表示UNKNOWN(未知):它不表示“”(空字符串)。对NULL这个值的任何比较都会生产一个NULL值。您不能把任何值与一个 NULL值进行比较，并在逻辑上希望获得一个答案。
>
> 使用IS NULL来进行NULL判断

### 12.主键、外键和索引的区别？

> 主键、外键和索引的区别
>
> 定义：
>
> > 主键--唯一标识一条记录，不能有重复的，不允许为空
> >
> > 外键--表的外键是另一表的主键, 外键可以有重复的, 可以是空值
> >
> > 索引--该字段没有重复值，但可以有一个空值
>
> 作用：
>
> > 主键--用来保证数据完整性
> >
> > 外键--用来和其他表建立联系用的
> >
> > 索引--是提高查询排序的速度
>
> 个数：
>
> > 主键--主键只能有一个
> >
> > 外键--一个表可以有多个外键
> >
> > 索引--一个表可以有多个唯一索引

### 13.你可以用什么来确保表格里的字段只接受特定范围里的值?

> Check限制，它在数据库表格里被定义，用来限制输入该列的值。
>
> 触发器也可以被用来限制数据库表格里的字段能够接受的值，但是这种办法要求触发器在表格里被定义，这可能会在某些情况下影响到性能。

### 14.说说对SQL语句优化有哪些方法？（选择几条）

> （1）Where子句中：where表之间的连接必须写在其他Where条件之前，那些可以过滤掉最大数量记录的条件必须写在Where子句的末尾.HAVING最后。
>
> （2）用EXISTS替代IN、用NOT EXISTS替代NOT IN。
>
> （3）避免在索引列上使用计算
>
> （4）避免在索引列上使用IS NULL和IS NOT NULL
>
> （5）对查询进行优化，应尽量避免全表扫描，首先应考虑在 where 及 order by 涉及的列上建立索引。　　
>
> （6）应尽量避免在 where 子句中对字段进行 null 值判断，否则将导致引擎放弃使用索引而进行全表扫描
>
> （7）应尽量避免在 where 子句中对字段进行表达式操作，这将导致引擎放弃使用索引而进行全表扫描

### 15.SQL语句中‘相关子查询’与‘非相关子查询’有什么区别？

> 子查询：嵌套在其他查询中的查询称之。
>
> 子查询又称内部，而包含子查询的语句称之外部查询（又称主查询）。
>
> 所有的子查询可以分为两类，即相关子查询和非相关子查询
>
> > （1）非相关子查询是独立于外部查询的子查询，子查询总共执行一次，执行完毕后将值传递给外部查询。
> >
> > （2）相关子查询的执行依赖于外部查询的数据，外部查询执行一行，子查询就执行一次。
>
> 故非相关子查询比相关子查询效率高

### 16.char和varchar的区别？

> 是一种固定长度的类型，varchar则是一种可变长度的类型，它们的区别是：

> > char(M)类型的数据列里，每个值都占用M个字节，如果某个长度小于M，MySQL就会在它的右边用空格字符补足．（在检索操作中那些填补出来的空格字符将被去掉）在varchar(M)类型的数据列里，每个值只占用刚好够用的字节再加上一个用来记录其长度的字节（即总长度为L+1字节）．

### 17.Mysql 的存储引擎,myisam和innodb的区别。

> 简单的表达：
>
> > MyISAM 是非事务的存储引擎；适合用于频繁查询的应用；表锁，不会出现死锁；适合小数据，小并发
> >
> > innodb是支持事务的存储引擎；合于插入和更新操作比较多的应用；设计合理的话是行锁（最大区别就在锁的级别上）；适合大数据，大并发。

### 18.数据表类型有哪些

> MyISAM、InnoDB、HEAP、BOB,ARCHIVE,CSV等。
>
> MyISAM：成熟、稳定、易于管理，快速读取。一些功能不支持（事务等），表级锁。
>
> InnoDB：支持事务、外键等特性、数据行锁定。空间占用大，不支持全文索引等。

### 19.MySQL数据库作发布系统的存储，一天五万条以上的增量，预计运维三年,怎么优化？

> a. 设计良好的数据库结构，允许部分数据冗余，尽量避免join查询，提高效率。
>
> b. 选择合适的表字段数据类型和存储引擎，适当的添加索引。
>
> c. mysql库主从读写分离。
>
> d. 找规律分表，减少单表中的数据量提高查询速度。
>
> e. 添加缓存机制，比如memcached，apc等。
>
> f. 不经常改动的页面，生成静态页面。
>
> g. 书写高效率的SQL。比如 SELECT \* FROM TABEL 改为 SELECT field\_1, field\_2, field\_3 FROM TABLE.
