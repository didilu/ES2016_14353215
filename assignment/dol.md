# DOL实例分析和编程
***
## dot实验结果图
修改example2，让3个square模块变成3个，修改完的example2.dot如下图所示：
![](http://a3.qpic.cn/psb?/V11g2aQW16thea/7vfrzNO5e1dOQhggh*HR4vKLJipNd04pTbC64mrI.uQ!/b/dAoBAAAAAAAA&bo=GQNaAgAAAAADAGc!&rf=viewer_4)
修改example1，使其输出3次方数，修改完的example1.dot如下图所示：
![](http://a3.qpic.cn/psb?/V11g2aQW16thea/dH7rDP6D7SFqAtC48JORJ4ux.XRm01m9iIGtnWOM0Kk!/b/dAoBAAAAAAAA&bo=*AHYAQAAAAADAAE!&rf=viewer_4)
## 具体步骤
1. 用“sudo su”获得root的权限，在root权限下进行一系列的操作
2. cd进入dol文件，再进入examples文件夹，ls可以查看该目录下有哪些文件，再进入到要修改的example2文件夹。可以看到这个文件夹里面有一个example1.xml文档，这是系统架构也就是模块连接方式的定义。example2文件夹里面还有一个src文件夹，在这个文件夹里，包含生产者、消费者和处理模块的.h以及.c文件。
3. 因为要把example2的模块变为两个，所以要在example2.xml里面修改，如下
![](http://a3.qpic.cn/psb?/V11g2aQW16thea/zx2aZwt.vb26Mr8yYM1lqR5YIFz2nloSVZNj30A6Ksk!/b/dHwBAAAAAAAA&bo=KwEXAAAAAAADABg!&rf=viewer_4)
4. 改完之后就要进行编译，这个时候需要进入编译的文件，所以执行语句cd/build/bin/main，并在这个目录执行语句“ant -f runexample.xml -Dnumber=2”
5. 编译成功就可以看到如图所示：
![](http://a1.qpic.cn/psb?/V11g2aQW16thea/CIiw*0MLY.fFQE6Ubm1UHgk9OurUg5M87wA.sRo.38A!/b/dHcBAAAAAAAA&bo=VwHDAQAAAAADALE!&rf=viewer_4)
6. 接着修改example1，因为之前已经对example1进行过编译，所以在这之前，需要把编译过的文件删除。然后再对square.c进行修改，使其变成3次方，修改如下：
![](http://a3.qpic.cn/psb?/V11g2aQW16thea/hVbUoo4U2DB.mGcoC*AGzo.UJHR7GykWwaeEND5r9hU!/b/dHABAAAAAAAA&bo=5AF6AAAAAAADALo!&rf=viewer_4)
然后执行语句cd/build/bin/main，进入到编译目录，执行语句“ant -f runexample.xml -Dnumber=1”
7. 编译成功就可以看到如图所示：
![](http://a1.qpic.cn/psb?/V11g2aQW16thea/udtiBp8cilSDkTkqEC0YMje3GJBqiS*7ZNUuLIWs2jY!/b/dHcBAAAAAAAA&bo=0AICAgAAAAADB*A!&rf=viewer_4)

## 实验感想
这次的实验操作比较简单，但是原理方面一开始了解的不是很清晰，只是按照要求执行语句跟修改代码。之后了解到每一个example里面，有src文件夹和一个该example的xml文件。在src文件里面，是生产者、消费者、处理模块等进程的功能的定义。xml文件是系统架构模块连接方式定义。src文件夹内包含2种文件.c和.h也就是实现的模块，就是.dot的框框的功能描述。（每个模块要实现 2个接口，xxx_init和xxx_fire两个函数， 分别是初始化这个模块做了什么，和这个模块运行的时候会做什么）。在example*.xml文件里定义了模块与模块之间是怎么连接的。在这个文件中，process就是dot图中的框，sw_channel线，connection是连接框和线
