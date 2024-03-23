+++
title = '在Mac系统上安装Java 7最佳实践'
date = 2014-09-16T14:02:10+08:00
draft = false
+++

截止今日，Oracle已经推出了JDK 8，对于这么新的版本，相信很多人和我一样不敢尝试。由于JDK 7已经在一些平台上（如最新的Android系统）得到支持，所以如果能在Mac上将JDK 6升级到7将会解决一些开发上的需求。

Mac系统历代OS都内置了JDK版本，不过最新的Mavericks上却只内置了JRE 6。Mac系统省缺JDK但是可以通过其升级机制安装JDK，遗憾的是苹果官方支持/安装的是JDK 6。看来Mac在Java的支持上有些滞后。幸运的是，在Mac上升级JDK很简单，可以按照如下步骤：

1. 前往Oracle官网的Java SE Development Kit 7下载页下载Mac平台的dmg安装包。由于Mac系统的处理器都是64位的，所以只有唯一对应的安装包可以选择！

2. 双击dmg安装包，会显示如下安装界面，双击pkg图标就会开始安装。

{{< figure src="/images/jdk7_installation_wizard.png" width="400px" height="560px" >}}


安装结束后在命令行输入：
```
java --version
```

回显：

```
java version "1.7.0_67"
Java(TM) SE Runtime Environment (build 1.7.0_67-b01)
Java HotSpot(TM) 64-Bit Server VM (build 24.65-b04, mixed mode)
```

Bingo，JDK 7已经安装完毕，不过先别急着离开，在实际的软件开发中，还会需要设置JAVA_HOME环境变量。

附加任务：设置JAVA_HOME环境变量

打开home目录下的.bash_profile文件，在最后加入如下代码：

```
export JAVA_HOME=$(/usr/libexec/java_home)
```

关闭文件后，在命令行输入：

```
source .bash_profile
```

这样，JAVA_HOME环境变量就设置完毕了，可以这样验证：

```
echo $JAVA_HOME
```

回显如下：

```
/Library/Java/JavaVirtualMachines/jdk1.7.0_67.jdk/Contents/Home
```

OK，大功告成！



