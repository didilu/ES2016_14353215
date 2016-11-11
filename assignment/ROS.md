# ROS的安装和配置
***
（Robot operation system，一套框架，底层提供硬件驱动，软件层面支持通用的文件格式。）
##1. 配置Ubuntu软件仓库
配置Ubuntu仓库，使得系统允许"restricted" "universe" 和"multiverse" 这三个repositories 。
##2. 设置自己sources.list
设置计算机，以接受来自packages.ros.org的软件。（ROS Jade只支持可信赖的Trusty (14.04), Utopic (14.10) and Vivid (15.04)为debian软件包。）
用如下的命令配置：
`sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'`
##3. 设置自己的密钥
用如下命令配置：
`sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116`
##4. 安装
第一步，确保自己的Debian软件包已经等新到最新的版本
`sudo apt-get update`
<br>
第二步，这里要特别注意，因为我的Ubuntu是14.04的，所以在安装依赖的时候，某些软件安装包可能会破坏服务器，所以按照如下的命令来安装依赖项：
`sudo apt-get install libgl1-mesa-dev-lts-utopic`
<br>
第三步，ROS提供了很多不同的库和工具。默认配置就有四种。<br>第一种就是Desktop-Full Install：ROS，rqt，rviz，机器人通用库，2D / 3D模拟器，导航和2D / 3D观感。这一次的ROS安装就是用的这一种配置。安装的命令是`sudo apt-get install ros-jade-desktop-full`。
<br>还有三种分别是Desktop Install：`sudo apt-get install ros-jade-desktop`;<br>
ROS-Base：`sudo apt-get install ros-jade-ros-base`<br>
Individual Package：就是安装一个独立的ROS包，比如`sudo apt-get install ros-jade-slam-gmapping`
##5. 初始化rosdep
在使用ROS之前，需要将之初始化rosdep。rosdep可以使得当我们想编译和需要去运行一些ROS的核心部分的时候，更容易地安装系统的依赖。<br>
`sudo rosdep init`<br>
`rosdep update`
##6. 环境设置
如果ROS的环境变量在每次一个新的shell加载的时候就会自动添加到bash命令中就会十分方便，所以使用以下命令来实现：<br>
`echo "source /opt/ros/jade/setup.bash" >> ~/.bashrc`<br>
`source ~/.bashrc`<br>
如果我们只是想为当前的shell改变环境：`source /opt/ros/jade/setup.bash`
##7. 获取rosinstall
rosinstall是ROS经常用到的命令行工具，通过一个命令就可以下载ROS软件包的许多源代码树。安装：`sudo apt-get install python-rosinstall`
##8. 建设farm status
##9. 获取安装包的源代码
`$ apt-get source ros-jade-laser-pipeline`<br>
但是这里必须指定一个单一的、确切的包名