---
title: Linux002 Bash基础
top: false
cover: false
toc: true
mathjax: false
categories: 
     - Tutorials
     - Linux
date: 2019-11-13 15:20:43
author: WenZhou
img:
coverImg:
password:
summary:
tags:
---

# Bash的基本使用

>在前面我们完成了Linux系统的基本安装，有的操作系统（如Ubuntu Manjaro Debian等）有 完整的图形界面 和 各种各样的 `GUI（Graphical User Interface，简称 GUI，又称图形用户接口）`工具。我们一下就能联想到windows的操作方式，所以你能快速上手这种linux发行版。但是，Linux真正的魅力在于一个看起来十分简陋，功能却异常强大的不起眼的小应用程序——Shell.本节我们就讲讲目前几乎所有发行版都预装的Shell的一种——`Bash Shell`。  
  
我们不讲各个发行版是怎样开机，登录的具体使用步骤，我相信你们有能力自己完成这些简单的click动作。

<!--more-->

## 我们先说说Shell

我们先直接抛出`shell`的定义，来源参考百度百科。

`shell` 是文字操作系统与外部最主要的接口。它是操作系统最外面的一层。shell管理你与`操作系统`之间的交互：等待你输入，向操作系统解释你的输入，并且处理各种各样的操作系统的输出结果。（还记得我们第一节课讲的操作系统就是一个**翻译官**吗？ 他其实更像一个大独裁者。Shell 是他的眼睛，耳朵，鼻子，嘴巴）。
我们给 操作系统（一个翻译官） 说我们想要干嘛，比如我们说 “播放我存放在d盘的电影《大话西游》”。这个翻译官通过耳朵（Shell）“听到”了我们的话，然后他就命令计算机说：

>"##%@￥&￥%@￥%#*&￥……%#&￥@￥#…………&*￥#……￥&@@%？?>{:<?"|}}{::>?++_*&$#%%!~!*(((&%@!!" （此处省略10k个字符）

来，让我给你翻译一下，就是 

>“去，把你磁盘上9527区的007到008分段的数据传输给 爱奇艺 ，爱奇艺，我再给你调用2个cpu的权限，你给我把画面播放到那个显示器上。”

总结一下，就是 操作系统通过耳朵（Shell）听我们给他的命令，然后他去用只有计算机硬件懂得的语言（当然我也懂，不然你就看不到上面那段人性化的翻译了）去命令计算机该怎么做。这些cpu，磁盘，显示器，音响都是操作系统的小弟，全由操作系统指挥。

其实Shell不仅仅是去”听”，他同时也能输出。在后续的实际操作我会给大家演示。

`Shell`大概就是这样，他是操作系统的最外部一层，用来管理我们和操作系统之间的交互。如果不把计算机内部细化。Shell也就是直接 ***管理人和机器的交互*** 的工具

Shell到后来又有了很多不同的版本出来，比如现在很出名的bash，zsh，其他的还有诸如sh，ksh，csh等等，你也可以在一个linux系统上安装很多不同的shell，不过今天我们不在这儿说怎样更换。因为还需一些其他的基础知识，不过我们还没有提。所以先缓缓。。

>很有必要讲一讲的是，shell和GUI的关系，要知道shell是早于GUI桌面应用很早很早之前就出来了的。你的电脑能做的事，都可以通过shell做到，而你的GUI桌面则不然，所以说，Shell的能力是>>>>GUI桌面的。学习shell也就很重要了。

## $ Bash

Bash啊，他是Shell的一种，目前的绝大多数Linux发行版都把Bash作为默认Shell。Bash的功能也比sh（shell的第一个版本）强大很多。

>在图形界面完备的Linux发行版中（如Ubuntu），你需要打开叫做`Terminal`(终端)的应用程序来操作Shell。
>
>简述：终端干的活儿是从用户这里接收输入（键盘、鼠标等输入设备），扔给 Shell，然后把 Shell 返回的结果展示给用户（比如通过显示器）。而 Shell 干的活儿是从终端那里拿到用户输入的命令，解析后交给操作系统内核去执行，并把执行结果返回给终端。更多内容，包括 terminal Shell tty 之间的联系和差别，[请移步此链接](https://www.cnblogs.com/sddai/p/9769086.html)

Bash和其他shell看起来差不多相同，黑底白字，偶尔出现漂亮鲜艳的红色（你绝对不会喜欢bash下出现红色的字的）。他大概长这样子，你看到的这整个框体就是terminal，里面的内容就是Bash了。

![](bash.png)

我们来看他的组成
```Shell
vvenzhou@ubuntu:~$
```
前面第一个字符串`vvenzhou`是你登陆的用户名
 * **@** 符号后面的`ubuntu`是你的计算机hostname，也就是计算机名
 * **：** 后面的是shell现在所处的目录位置（这里的`~`就是指当前的用户目录）
 * **$**  后面就是你输入shell命令的地方

### 初识命令（command）

下面有一些常用的shell命令（我相信你们都能看懂初中英语吧）
![](commands.png)
我们试着输入一些命令，看看shell有什么反应
```Shell
vvenzhou@ubuntu:~$ ls
```
![](ls.png)

`ls`命令表示显示出当前目录下的文件。还记得当前目录是怎么看的吗？

一般的，一个新的Linux系统会自动在用户目录下创建好这么几个目录（windows下叫做文件夹）（folder）。

shell命令有的只需要单独command名就行了，如上面的`ls`，然而还可以在后面带上参数（arguments），***命令和参数之间用空格分开*** 。比如
```Shell
vvenzhou@ubuntu:~$ ls Pictures
```
![](ls_01.png)

这表明 显示 *当前目录* 下的 *Pictures*目录下的文件。即 `~/Pictures/`
你也可以直接跟一个完整的路径
```Shell
vvenzhou@ubuntu:~$ ls ~/Pictures
```
![](ls_02.png)

如果路径不正确（目录不存在）呢？
```Shell
vvenzhou@ubuntu:~$ ls ~/Pict
```
![](ls_03.png)

shell会返回错误信息。

然而`ls`还能做更多的东西，你可以在命令后面加指定的option来实现更多的功能，试试在 `ls` 后面加上 `-a` （缩写） 或者 `--all` （全称）
***同理，command option argument之间都要用空格分开***
```Shell
vvenzhou@ubuntu:~$ ls -a
```
![](ls_04.png)

看！他显示了更多的东西。不仅有那些目录，还有更多的其他东西。
`ls` 默认只显示那些不是`.`开头的文件和目录。但是你可以加上`-a` option来告诉`ls`你想看到更多。

你还可以把好多option写在一起，试试用`ls -al`代替`ls -a -l`。
```Shell
vvenzhou@ubuntu:~$ ls -al
```
![](ls_05.png)
（至于-l option的作用我暂时不讲）

这些就是命令（command）的基本使用方法。现在去自己的Linux上试试上面那个表中的命令吧，更多命令及使用方法[请移步本系列教程的另一个帖子](https://osa-null.github.io/[object%20Object]/Linux/Linux_general/)。**注意要细心观察输入了命令后的种种变化**。

如果你不知道某个命令该怎么用，有哪些option，需要什么argument，请使用`man` 命令，如`man ls` `man man`。要退出 man 请注意终端下方的高亮提示。

Linux是个高度自由的操作系统，也请大家多多锻炼动手能力，自己发现错误，找到错误，解决错误的过程才是你真正学习Linux知识的时候。

Linux学习之路的3条建议
* 善用man命令
* 善用 [Baidu](https://www.baidu.com) [Bing](https://www.bing.com) 以及[某404网站](https://www.google.com)。
* 学好英语

如果你去各个渠道都找不到解决办法，欢迎来找我或者其他人，虽然我肯定也不会（你在网上都找不到了，我也一定找不到），但我们可以一起来尝试解决它。交流出真知，别忘了，我们有强大的开源社区！！！

>more tips：shell可以运行的不仅仅是一些自带命令哦，所有可执行文件（通俗的说就是应用程序）都可以通过shell打开。

### One more thing 

上面讲的那些我相信大家都很容易就明白了，而且确实也不难，不如我们就再加一点点料，补充一点理论知识。我们就讲讲Linux的文件系统，这就涉及到了Linux的一个理念——***万物皆是文件***

#### Everything is a file

>"On a UNIX system, everything is a file; if something is not a file, it is a process."

Linux 中所有内容都是以文件的形式保存和管理的，即一切皆文件，普通文件是文件，目录（Windows 下称为文件夹）是文件，硬件设备（键盘、监视器、硬盘、打印机）是文件，就连套接字（socket）、网络通信等资源也都是文件。

那么问题来了，要如何来管理这些庞大的各类文件呢？

树！

树其实很简单，就是长得像树的一种文件系统，首先是根目录`/`，这是唯一的，你可以理解成所有目录的老大，没有谁能在他之上（之前）了。根目录下面便是各类子目录，具体见下图。

![file system](file_system.png)

每个目录都有他们特定的功能，比如
![partition](partition.png)

记得`~`这个地址吗？如果我登录的用户名是`wenzhou`，那么这个波浪线的完整地址其实就是`/home/wenzhou/`，那里就是存我这个用户的资料的，比如我下载了什么电影，音乐，电子书，都应该放在自己的用户目录下，以免造成磁盘文件的混乱。

>如果你想要知道你当前所在目录的完整地址，除了看shell前面的那一坨东西之外，也可以用`pwd`命令来查看，去试试。

>还有，注意`/root`和`/`，他两肯定不一样，但是我们读起来都是读的 “gen mu lu” ，要注意区分他俩，别混淆了。

更多的细节：（我就不翻译了）
![more details](partitions_desc.png)

Well, bash基础和Linux文件系统大概就讲这些，更具体的可以查看我们发到群里的intro-linx.pdf获取更多知识。

goodbye！