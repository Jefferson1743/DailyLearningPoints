# Java

## Class 文件结构
Java 代码经过编译成字节码文件，ClassLoader将字节码load到常量池中。在堆上实例化对象。
![](./.img/JavaRunProcess.png)
字节码文件的结构包括：魔数、次版本号、主版本号、常量池、访问标志、类名、父类名、接口、属性、方法区、其他属性表（可以通过jclasslib插件）
![文件结构](./.img/JavaStructure.png)
+ 常量池：所有的引用和属性名都是存储在常量池，后续通过索引引用。
![](./.img/ConstantPool.png)
![](./.img/ConstantPoolExample.png)

+ 方法区：
    - “Code区”：源代码对应的JVM指令操作码，在进行字节码增强时重点操作的就是“Code区”这一部分。
        + stacks
        + locals
        + args_size

    - “LineNumberTable”：行号表，将Code区的操作码和源代码中的行号对应，Debug时会起到作用（源代码走一行，需要走多少个JVM指令操作码）。

    - “LocalVariableTable”：本地变量表，包含This和局部变量，之所以可以在每一个方法内部都可以调用This，是因为JVM将This作为每一个方法的第一个参数隐式进行传入。当然，这是针对非Static方法而言。

    - JVM的指令集是基于栈而不是寄存器，基于栈可以具备很好的跨平台性（因为寄存器指令集往往和硬件挂钩），但缺点在于，要完成同样的操作，基于栈的实现需要更多指令才能完成（因为栈只是一个FILO结构，需要频繁压栈出栈）。另外，由于栈是在内存实现的，而寄存器是在CPU的高速缓存区，相较而言，基于栈的速度要慢很多，这也是为了跨平台性而做出的牺牲。操作码或者操作集合，其实控制的就是这个JVM的操作数栈。为了更直观地感受操作码是如何控制操作数栈的，以及理解常量池、变量表的作用。
## ClassLoader 工作机制
### 类加载
[参考链接](https://www.cnblogs.com/rmxd/p/15187685.html)
ClassLoader是Java的核心组件，所有的Class都是由ClassLoader进行加载的，ClassLoader负责通过各种方式将Class信息的二进制数据流读入JVM内部，转换为一个与目标类对象的java.lang.Class对象实例，然后交给JVM进行链接、初始化等操作。因此，ClassLoader在整个装载阶段，只能影响到类的加载，而无法通过ClassLoader去改变类的链接和初始化行为。至于它是否可以运行，则由执行引擎决定。
![类加载机制](./.img/loadClassTOJVM.png)
### ClassLoader分类

![双亲委派机制](./.img/classLoaderStruture.png)
1. 引导类加载器（Bootstrap ClassLoader）： 该类由C/C++语言实现，嵌套在JVM内部；用来加载Java核心库（JAVA_HOME/jre/lib/rt.jar或sun.boot.class.path路径下的内容）；出于安全考虑，只加载包名为java、　　　　javax、sun等开头的类 
2. 扩展类加载器（Extension ClassLoader） java语言，sun.misc.Launcher.$ExtClassLoader实现，继承于ClassLoader类，父类加载器为启动类加载器；从JAVA_HOME/jre/lib/ext子目录下加载类库 
3. 系统类加载器（AppClassLoader） java语言，sun.misc.Launcher.$AppClassLoader实现，继承于ClassLoader类，父类记载器为扩展类加载器；它是用户自定义类加载器的默认父加载器

4. 自定义类加载器：

　　（1）在Java日常应用程序开发中，类的加载几乎是由上述3类加载器相互配合执行的。在必要时，我们还可以自定义类加载器，来定制类的加载方式

　　（2）体现Java语言强大生命力和巨大魅力的关键因素之一便是Java开发者可以自定义类加载器来实现类库的动态加载，加载源可以是本地Jar包，也可以是网络上的远程资源。

　　（3）通过类加载器可以实现非常巧妙的插件机制，这方面的实际应用案例举不胜举。例如Eclipse的插件机制。类加载器为应用程序提供了一种动态增加新功能的机制，这种机制无须重新打包发布应用程序就能实现

　　（4）自定义类加载器能够实现应用隔离，例如tomcat、spring等中间件和组件框架都在内部定义了自定义的类加载器，并通过自定义的类加载器隔离不同的组件模块。这种机制比C/C++程序要好太多，想不修改C/C++程序就能为其新增功能，几乎是不可能的，仅仅一个兼容性便能阻挡住所有美好的设想。

　　（5）自定义类加载器通常需要继承于ClassLoader
### 类加载方式
类的加载方式：虚拟机将编译后的字节码文件加载到内存的方式。

1. 显式加载
Java代码通过调用ClassLoader加载class对象。
```java
Class.forName(String name);
this.getClass().getClassLoader().loadClass()
```
2. 隐式加载

Java中没有明确的调用加载代码，通过JVM自动加载到内存。
```java
加载某个类时，该类引用了另一个类的对象。
User u = new User();
```

#### 区别
1. 隐式加载能够直接获取对象的实例，而显式加载需要调用 Class 对象的 newInstance() 方法来生成对象的实例。

2. 隐式加载能够使用有参的构造函数，而使用 Class 对象的 newInstance() 不支持传入参数，如果想使用有参的构造函数，必须通过反射的方式，来获取到该类的有参构造方法。

3. 显式加载常用在反射，使用更为灵活，可以一个代码对应很多个类，根据传入的class类的名称映射为不同的实现类。

### 命名空间
1. 每个类加载器都有自己的命名空间，命名空间由该加载器及所有的父加载器所加载的类组成

2. 在同一命名空间中，不会出现类的完整名字（包括类的包名）相同的两个类

3. 不同的命名空间中，有可能会出现类的完整名字（包括类的包名）相同的两个类

```txt
在大型应用中，我们往往借助这一特性，来运行同一个类的不同版本。　　

对应任意一个类，都需要由加载它的类加载器和这个类本身一同确认其在Java虚拟机中的唯一性。

每一个类加载都拥有一个独立的类名称空间：比较两个类是否相等，只有在这两个类是同一个类加载的前提下才有意义！否则，即使这两个类源自同一个Class文件，被同一个虚拟机加载，只要加载他们的类加载器不同，那么这两个类就必定不相等。
```
### Class.forName 和 ClassLoader的区别
- loadClass() 方法获得的 Class 对象只完成了类的加载，后续的初始化等操作均未进行。
- 使用 Class.forName() 方法获得 Class 对象，完成了类加载过程各个环节，并执行完类初始化工作。

### 双亲委派机制

双亲委派模型。但不是所有类加载都遵守这个模型，有的时候，启动类加载器所加载的类型，是可能要加载用代码的。例如JDK内部的SPI机制，用户可以在标准API框架上，提供自己的实现，JDK也需要提供默认的参考实现。比如JDBC、JNDI等很多方面都是利用这种机制，这种情况就不会使用双亲委派模型去加载，而是利用所谓的上下文加载器。

定义：如果一个类加载器在接到加载类的请求时，它首先不会自己尝试去加载这个类，而是把这个请求任务委托给父类加载器去完成，依次递归，如果父类加载器可以完成类加载任务，就成功返回，只有父类加载器无法完成此加载任务时，才自己去加载。（“典型啃老族”）

本质：规定了类的加载顺序：引导类加载器先加载，若加载不到，由扩展类加载器加载，若还加载不到，才会由系统类加载器或者自定义的类加载器进行加载。

优势：避免了类的重复加载，确保一个类的全局唯一性；保护程序安全，防止核心API被随意篡改

结论：由于Java虚拟机规范并没有明确要求类加载器的加载机制一定要使用双亲委派模型，只是建议采用这种方式而已。比如在tomcat中，类加载器所采用的加载机制就和传统的双亲委派模型有一定区别，当缺省的类加载器接收到一个类的加载任务时，首先会由它自行加载，当它加载失败时，才会将类的加载任务委派给它的超类加载器去执行，这同时也是Servlet规范推荐的一种做法。


### java -Xbootclasspath
[参考链接](https://blog.csdn.net/hongfenglx/article/details/108807239)
当用java -jar yourJarExe.jar来运行一个经过打包的应用程序的时候，你会发现如何设置-classpath参数应用程序都找不到相应的第三方类，报ClassNotFound错误。实际上这是由于当使用-jar参数运行的时候，java VM会屏蔽所有的外部classpath,而只以本身yourJarExe.jar的内部class作为类的寻找范围。
解决方案

一 BootStrap class扩展方案

Java 命令行提供了如何扩展bootStrap 级别class的简单方法.
-Xbootclasspath: 完全取代基本核心的Java class 搜索路径.
不常用,否则要重新写所有Java 核心class
-Xbootclasspath/a: 后缀在核心class搜索路径后面.常用!!
-Xbootclasspath/p: 前缀在核心class搜索路径前面.不常用,避免
引起不必要的冲突.

语法如下:
(分隔符与classpath参数类似，unix使用:号,windows使用;号，这里以unix为例)
java -Xbootclasspath/a:/usrhome/thirdlib.jar: -jar yourJarExe.jar

二 extend class 扩展方案

Java exten class 存放在{Java_home}\jre\lib\ext目录下.当调用Java时,对扩展class路径的搜索是自动的.总会搜索的.这样,解决的方案就很简单了,将所有要使用的第三方的jar包都复制到ext 目录下.

三 User class扩展方案

当使用-jar执行可执行Jar包时,JVM将Jar包所在目录设置为codebase目录,所有的class搜索都在这个目录下开始.所以如果使用了其他第三方的jar包,一个比较可以接受的可配置方案,就是利用jar包的Manifest扩展机制.
步骤如下:

1.将需要的第三方的jar包,复制在同可执行jar所在的目录或某个子目录下. 比如:jar 包在 /usrhome/yourJarExe.jar 那么你可以把所有jar包复制到/usrhome目录下或/usrhome/lib 等类似的子目录下.

2.修改Manifest 文件

在Manifest.mf文件里加入如下行

Class-Path: jar1-name jar2-name directory-name/jar3-name

Class-Path 是可执行jar包运行依赖的关键词.详细内容可以参考 http://java.sun.com/docs/books/tutorial/deployment/jar/downman.html 。要注意的是 Class-Path 只是作为你本地机器的CLASSPATH环境变量的一个缩写，也就是说用这个前缀表示在你的jar包执行机器上所有的CLASSPATH目录下寻找相应的第三方类/类库。你并不能通过 Class-Path 来加载位于你本身的jar包里面（或者网络上）的jar文件。因为从理论上来讲，你的jar发布包不应该再去包含其他的第三方类库（而应该通过使用说明来提醒用户去获取相应的支持类库）。如果由于特殊需要必须把其他的第三方类库（jar, zip, class等）直接打包在你自己的jar包里面一起发布，你就必须通过实现自定义的ClassLoader来按照自己的意图加载这些第三方类库。

以上三种方法推荐第一种，扩展性好，操作起来也最方便.

Java的安全机制随不同的JDK版本有不同的变化,会影响很多核心CLASS,比如Thread,所以很多大型商业软件,要求JDK的版本很严格.部分原因也在此.这也要求在发布自己编写的应用时候,不管大小,都要说明开发和测试的JDK版本.


## Javac 编译原理

## JVM 体系结构与工作方式

## 内存管理