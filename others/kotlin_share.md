---
title: 【来自兄弟连】kotlin笔记
tags: kotlin
---
## day1 从谷歌IO2017看开发行业趋势
### 前提

-   老的编程语言真的都不太好用了吗？
-   为什么各大公司推出的新的编程语言又没有起来呢？
-   想成就未来十年的技术生涯,今天的沙龙你不容错过！
    今晚八点请锁定本群，龙哥带你从谷歌IO2017看开发行业趋势，精彩不容错过哦~~-

### 开始

1.  好吧，那回归正题，这次的KT语言又有什么不同呢？会不会又是官方拼命推而市场不动？

2.  我的判断是不会，固然大部分程序员都有惰性，固然很多人不愿意放弃自己的开发习惯去学习新的知识，固然java开源生态很好。

3.  没错，java开源生态真的很好，都说java是三流的语言+一流的生态，比如大名鼎鼎的hadoop及hadoop生态的众多软件，比如最流行的消息队列RabbitMQ，比如强大的搜索引擎lucene等等，不计其数的优秀开源项目。

4.  是什么支持java这么多年屹立不倒，正是因为开源，如果你选择放弃了java，就代表你放弃了成千上万人数十年来的积累，这么大的代价你会选择放弃吗？

5.  回到今天的主角KT语言，它和之前提到的新的编程语言截然不同，为什么？因为有jvm的存在。

6.  Jvm是java运行的基础，java语言经过javac编译之后生成了一的不是直接在机器上运行的机器码而是一种叫字节码的东西，物理机上运行着jvm虚拟机，而虚拟机上在运行字节码，那么这就为聪明的开发者留出了足够的想象空间。4.

7.  Java编译器可以把java编译成jvm能识别的字节码，那么创造出一种新的语法以及编译器出来，编译出同样可以被jvm识别的字节码应该是完全可行的。

8.  基于这一理论，java社区的大牛们作出了很多伟大的创造，比如Scala与Clojure，groovy，它们都融入了大量先进的语言特性，另外还有ruby与java社区基于jvm开发了jruby，让ruby先进的语法在java生态中获益。

9.  Kotlin语言也是这样一个语言，但它和上面提到的语言不同，除了能运行与jvm之中，他还能做到100%和java交互，无论是oracle jdk 环境下的 java还是android，它是强类型的，但是提供了更多的语法糖，他使用起来更便捷，而且jdk8以上版本的java也提供了函数式编程的支持，这使得java完整的生态可以被kt使用。

10. 好吧，听到这里，你大概应该能感受到kt与之前其他语言不同的地方，他不会和之前的java竞争冲突，反而会让java社区更加迅速的发展。

11. 可以跟大家说一下的是，早在两年前，java最强的依赖管理Gradle就开始使用Kt开发相应的分支，并推广使用。

12. 如果是java程序员，对于KT语法并不会太抵触，因为他依然可以很好的按照你java的设计模式工作，但是它却能大幅减少java程序员的编码量。

13. 其他语言的开发者如果想获得java社区的资源优势，从0学java代价太大，但是如果你稍微投入精力，你就会发现KT上手非常容易，这也为其他开发者进入java生态带来了巨大的机会。

14. 另外KT还能在没有JVM的环境下，编译成js，再加上android支持，以及jetbrains提供的IOS开发能力的支持，它将是一个优秀的全栈开发语言。11.

15. 那么我们就来看看它的语法吧
    `新建一个文本文档 命名为 hello.kt`
    `输入以下内容`

    >     fun main(args: Array<String>) {
    >         println("Hello, world!")
    >     }

    然后就可以编译和运行这个程序了，编译后也可以打包成java JAR包
    不知道大家发现没有，现代化的语言都可以是不带分号的，也不再要求强制面向对象模式，这点和java不同，java的所有函数都需要在类里面，而KT不需要。

16. Java在字符串处理上的落后是让我最头痛的问题之一，不过这下子好了

    >     fun main(args: Array<String>) {
    >         if (args.size == 0) {
    >             println("Please provide a name as a command-line argument")
    >             return
    >         }
    >         println("Hello, ${args\[0\]}!")
    >     }

17. 大家可以看到熟悉的模版字符串功能，这一点点的改善，能给我们在开发过程中带来巨大的好处。
    循环也更简单了，

    >     fun main(args: Array<String>) {
    >         for (name in args)
    >         println("Hello, $name!")
    >     }

18. 再看看条件输出，如果用java，是不是代码要多出很多呢

    >     fun main(args: Array<String>) {
    >         val language = if (args.size == 0) "EN" else args\[0\]
    >         println(when (language) {
    >             "EN" -&gt; "Hello!"
    >             "FR" -&gt; "Salut!"
    >             "IT" -&gt; "Ciao!"
    >             else -&gt; "Sorry, I can't greet you in $language yet"
    >         })
    >     }

19. 类的定义也是很简洁的

    >     class Greeter(val name: String) {
    >         fun greet() {
    >             println("Hello, ${name}");
    >         }
    >     }
    >         fun main(args: Array<String>) {
    >             Greeter(args\[0\]).greet()
    >     }

#### 当然，还有更多更好的高级特性，今天在这里就不一一介绍了，后面有机会的话，我会带领大家尝试一下使用KT开发web项目和移动项目，体验更多的好处。

#### 我相信使用KT，我们必会从中受益。

day2
----

### 前提

直播八点准时开始哦~~
本期主题【拥抱java大生态，快速上手kotlin开发】
今晚文字直播，周围有对此话题感兴趣的童鞋，也可以拉进群共同交流

### 开始

1.  上次的分享，我向大家介绍了一下kotlin语言的一些基本特点与市场环境，我们能清楚的看到，java大生态的优势。hadoop 、elasticsearch、rabbitmq等一系列的开源产品与社区成就让java在兵器谱上排名屹立不倒，简直就是羡煞旁人。
2.  被谷歌选择的Kotlin语言可以认为是java的一次升级，这次升级不同于groovy等同样运行与jvm的动态语言，保持静态类型使得他完整的支持java的一切却没有损失效率。
3.  Kotlin是java的kotlin，因为java程序员使用它几乎不需要什么额外的付出，一切都不用变，却能收获开发效率的大幅提升。
4.  Kotlin也是其他所有互联网与移动互联网开发者的福音，无论你是python还是ruby程序员又或者你之前一直在写php，你会发现从kotlin开始入手绝对是一件性价比超高的事情，因为我们不需要完整的去学习老旧的java体系知识就能拥抱java的大生态。
5.  是的，kotlin这么优秀，我们要怎么样开始呢？
6.  Kotlin目前为止中文资料还不多，并且国内第一批kt语言的开发者都是那些经验丰富的大牛级别的java程序员，那么其他语言的开发者如果想要拥抱java生态应该从哪里开始，小白java程序员又该从哪里开始呢？
7.  考虑到这些实际问题，我决定从今天开始，持续为大家能快速上手kt语言项目开发做点贡献。
8.  我不打算从语法基础开始讲程序逻辑，相信关注我的技术沙龙分享的同学对于什么是顺序、循环和分支以及什么是函数以及什么是对象还是能分的很清楚的。
9.  我会从最基础的开发环境搭建开始，手把手带着大家从零开始搭建起环境，并掌握一个商业项目开发过程中所需要的全部知识与技巧。
10. 我知道完成这样一件事情并不容易，也希望大家多多支持，我将把我的经验汇聚成文字持续的在我的微博和微信连载，并在完成全部内容后将整理的资料整理成书籍，大家按照我的教程去做的过程中如果发现有问题希望大家能及时的向我反馈，帮助我更好的完成这这个任务。
11. 书名还没有想好，暂定为《拥抱java大生态，快速上手kotlin开发》又或者叫《kt语言入门》，当然大家也可以在微博中给我一些建议。
12. 先把我准备的第一章内容贴出来
13. 开发环境
    kotlin语言能编译成jvm环境下运行的字节码，同时也能在没有jvm的时候编译成javascript，不过本书并不是要详细介绍kt语言的方方面面，相信大部分人选择kt是因为java出色的生态。想想看，能用更简洁且优雅的语法拥抱java的大生态必定是一件美妙的事情。
    因此，要跟随本书一起学习，首先就必须要安装java环境。

14. 安装JDK
    一个打包好的kt程序，在任何一台安装有jdk的机器上都可以运行（从jdk6开始支持），不过为了能使用java社区的最新成果，我们应该至少安装jdk8或者更高版本的java（java8支持函数式编程）。
    在这里你可以找到最新的jdk：
15. <http://www.oracle.com/technetwork/java/javase/downloads/index.html>
16. 安装完jdk，紧接着我们需要配置我们的环境变量 JAVA\_HOME 并把JAVA\_HOME下的bin目录添加到系统环境PATH下，这样一来，你就可以在任何地方运行java命令了。
17. 打开终端测试一下，输入

    >     java -version
    >
    >     java version "1.8.0\_131"

    >     Java(TM) SE Runtime Environment (build 1.8.0\_131-b11)
    >     Java HotSpot(TM) 64-Bit Server VM (build 25.131-b11, mixed mode)

    能正常显示出java的版本，证明java安装成功。

18. 安装Kotlin
    如果你不是只想运行kt程序，而是希望自己编写kt程序并打包编译应用程序，那么你就需要安装kotlin的开发运行环境了。19.
19. 在线IDE
    为了方便开发者，KT官网提供了在线IDE环境，帮助开发者快速实验KT语法。只要访问https://try.kotlinlang.org/就可以开始KT语言的学习了。
20. 手动安装
    但希望自己动手编写具有实用功能的项目，我们还是需要在本机来安装KT的编译器，编译器的源码托管在github，可以从 [https://github.com/JetBrains/kotlin/releases/下载最新版本的编译器](https://github.com/JetBrains/kotlin/releases/下载最新版本的编译器)。
    将独立编译器解压缩到目录中，并可选择将bin目录添加到系统路径。该bin目录包含在Windows，OS X和Linux上编译和运行Kotlin所需的脚本。
21. SDKMAN
    如果手动安装觉得太麻烦，可以选择使用SDKMAN，这也是作者比较推荐的做法，因为在实际开发过程遇到的许多软件都可以用SDKMAN来管理。
    如果机器里面安装了SDKMAN，那么只需要一条命令 就可以安装好Kotlin了。 sdk install kotlin
22. Homebrew
    苹果电脑上Homebrew是一个很好的工具，使用Homebrew安装软件之前最好先更新一下资源，因此只要键入如下两条命令就可以安装Kotlin了。

    brew update

    brew install kotlin
验证开发环境
输入

    kotlin -version
如果你手动安装并正确配置了环境变量，那么这条命令将会显示Kotlin的版本信息，不过你也可能会得到一条类似的出错信息

    error: no build.txt was found at home=/usr/local/Cellar/kotlin/1.1.2-2/libexec
遇到这条信息不要担心，这是Homebrew安装版的一个小bug，对你的程序运行没有什么实质影响。

1.  所有的编程语言教材都喜欢从输出一个 “Hello ，World！”开始，我们既然要开始编写一个不需要太动脑经又具有深刻意义的程序，也就不能免熟了。
2.  新建一个文本文件输入以下内容

    fun main(args: Array&lt;String&gt;) {

        println("Hello, World!")

}
将文件命名为hello.kt，然后打开终端（在windows里面则输入win+R键在运行对话框中输入cmd），进入代码文件所在目录，然后输入

    kotlinc hello.kt -include-runtime -d hello.jar
如果有过java开发经验的技术人员肯定知道，java命令用来执行java程序，javac命令用来编译java项目，而在这里kotlinc则用来编译kotlin程序，不过执行程序不需要kotlin，因为刚才的命令已经把hello.kt编译并打包成了hello.jar，因此输入

    java -jar hello.jar
我们就可以看到程序的运行结果。

1.  在这里有一些事情是我们需要注意的，我们在刚才的编译过程中加入了 -include-runtime参数，这个参数会把kotlin的运行时需要依赖的jar包一起打包起来，也正因为如此，我们才能直接用java -jar命令来运行hello.jar。
2.  如果你在编译过程中使用如下命令编译就会得到很不一样的结果

    kotlinc hello.kt
没有-d参数就不会打包，那么hello.kt只会被编译成 HelloKt.class文件（注意类名称，不是hello，而是HelloKt），因为没有加入-include-runtime参数，所以HelloKt.class就只是一个普通的类，没有包含KT的运行时环境，如果要运行这个程序，就需要使用kotlin命令

    kotlin HelloKt
如果使用java命令执行就会报错，如果你的终端支持显示中文，那么你会看到

    错误: 找不到或无法加载主类 HelloKt.class
我们知道，在实际开发中，如果我们编写的是某个类库，给其他程序调用的，那么我们就不应该加入运行时环境，只需要-d参数打包即可。

1.  我们应该在程序打包的时候把运行环境打包进来，kotlin的运行时环境很小，并不会给项目带来负担。不过即便整个应用程序一起打包的时候没有把运行时环境打包进来也不是不能运行，但是这种情况下，我们需要去配置程序运行的class path，而这样我们的程序就无法很好的迁移，因此不推荐这样做。
2.  另外大家也可以尝试一下直接输入 kotlinc 不带任何参数，你将会进入到一个交互模式，在交互模式下，你可以快速的验证你学习到的语法。
3.  内容将持续在技术沙龙以及我的微博 微信公众号进行连载，大家可以关注一下，也希望大家帮助传播
4.  

day3
----

### 前提

### 开始

day4
----

### 前提

### 开始

day5
----

### 前提

### 开始
