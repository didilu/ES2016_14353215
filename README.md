# ES2016_14353215
###Description
***
####
DOL是distributed operation layer的简写，意思是分布式操作层。DOL是一个框架，可以将应用（半）自动映射到多处理器架构平台。它主要由三部分组成:1.DOL应用程序接口：DOL定义了一组计算和通信的例程，使编程分布式，使得图形平台有并行应用程序。使用这些例程，应用程序员可以编写程序，没有详细的知识关于底层架构。事实上，在硬件相关的软件这些例程都有待进一步细化（HDS）层。2.DOL功能仿真：为程序员提供了一个能测试他们应用程序的可能性，已经形成了功能仿真框架。除了应用功能验证，这框架用于在应用层面获得性能参数。3.DOL映射优化：目标的DOL映射优化计算一组最优映射应用到形状架构平台。在 第一步，基于XML的规范格式已被定义，允许描述在抽象的层面上的 应用和架构。然而，所有的信息来获得准确的性能估计是必要的包含。DOL允许基于Kahn过程网络模型计算的指定应用和基于SystemC特化仿真引擎。而且DOL还提供了一个基于XML的规范格式来描述在一个并行应用在多处理系统上的运行，包括绑定和映射。
###How to install
***
####
1. 升级原有的软件。
2. 安装ant，ant是一种基于java的build工具，用java的类来扩展，它本身就是一个流程脚本引擎，用来自动化调用程序完成项目的编译，打包和测试等。ant有很多优点，跨平台性，因为是纯java语言编写的，所以有很好的跨平台性。操作简单，ant是由一个内置任务和可选任务组成的。Ant运行时需要一个XML文件(构建文件)。ant容易维护和书写，结构清晰。ant可以集成到开发环境中。
3. 安装openjdk-7-jdk。JDK 是Java开发工具包 (Java Development Kit ) 的缩写，它是一种用于构建在 Java 平台上发布的应用程序、applet 和组件的开发环境。其中包括了Java编译器、JVM、大量的Java工具以及Java基础API里面是Java类库和Java的语言规范。javac命令用来编译java文件，java命令可以执行生成的class文件。
4. 安装unzip，就是一个解压缩软件。
5. 把需要用到的dol_ethz，jdk等文件拷贝到ubuntu上，或者在ubuntu上面用命令行找到网站并在网站上下载。注意要把网址输入正确，在下载的过程中保持网络的通畅。
6. 用指令mkdir来创建一个文件夹dol，这个文件夹dol等下用来放解压dol_ethz的文件，解压的指令是unzip。解压systemc用tar -zxvf systemc-2.3.1.tgz。
7. 用cd命令进到systemc-2.3.1的目录再用一个mkdir的命令新建一个文件夹，然后用../configure CXX=g++ --disable-async-updates 来运行configure，可以得到<br>![picture1](https://cl.ly/3w1n1z2f2g3y/download/Image%202016-10-09%20at%2010.19.27%20PM.png)<br>
8. 然后执行make install进行编译，编译之后用pwd来得到当前的工作路径。我的到的当前工作路径是： /home/ludi/systemc-2.3.1
9. 进入刚才的dol文件夹，通过sudo gedit来修改build_zip.xml文件中的注意查看自己的ubuntu系统我的是32位的，所以不需要改成lib-linux64。
10. 通过命令sudo $ ant -f build_zip.xml all来编译，成功显示build successful。然后运行第一个例子，注意要进入到build/bin/mian里面，用命令sudo ant -f runexample.xml -Dnumber=1 成功得到如下图所示。<br>![picture](https://cl.ly/0l381M0y380j/download/Image%202016-10-09%20at%2010.19.58%20PM.png)<br>
###Experimental experience
***
####
1. 再次用到虚拟机和ubuntu，一开始以为一定要升级ubuntu，所以在终端执行sudo apt-get update指令后，问我要不要升级我就升级了，但是升级之后就出现问题了。首先是升级完只有命令行界面，所以我查了怎么进入图形界面，但是一直进不去，我又查了怎么下载。下载之后还是一直进不去图形界面。所以只好把ubuntu卸载了，重新下载一个镜像再重新安装。在安装过程中又遇到太奇奇怪怪的问题。反正折腾了大概四次才把ubuntu重新安装上。
2. 开始配置一开始就是安装一些必要的环境，在安装的时候没有遇到很大的问题，不过后来配置失败显示应该是jdk安装不好。之后还是比较顺利的，但是要记得最好都用root权限。
3. 到了运行example1的时候就没有build成功，之后一直找了很多原因，还换过源，但最后发现是中文系统的问题，中文系统需要在dol/build/bin/main 下 的 runexample.xml里面注释掉一段代码：<br>
    `<tstamp>`
     ` <format property="touch.time"
              pattern="MM/dd/yyyy hh:mm aa"
              offset="-5" unit="second"/>`
    `</tstamp>`

    `<touch datetime="${touch.time}">`
      `<fileset dir="example${number}"/>`
    `</touch>`
4. 通过这次实验认识到了DOL框架，也初步认识了Gig和GitHub仓库，对markdown语法有了初步了解，不过还要在后续的实验中继续加强。
