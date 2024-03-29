---
title: 面向数据设计 | Data-Oriented Design 第一节
date: 2021-12-09 22:09:05
categories: [Translation,DODBook]
tags: [DOD, 面向数据, Programming] 
---

DOD Book 译注稿 | 第一节 面向数据设计 Data-Oriented Design
<!-- more -->

## 面向数据设计 | Data-Oriented Design

面向数据设计其实已经以种种不同形式存在了数十年，但直到2009年9月Noel Llopis在其同名文章[Data-Oriented Design](https://gamesfromwithin.com/data-oriented-design)中才被正式命名。

面向数据设计是否算是一种编程范式，尚且存在一些争议。许多人认为它是与其他编程范式（面向对象、面向过程或是函数式编程）并行使用的。这个观点在某些方面没错，面向数据设计是可以与其他范式一起发挥作用，但这并不意味着它不能成为一种编程的指导思想。毕竟其他编程范式或多或少也能在一定程度上相互配合。Lisp程序员知道函数式编程可以和面向对象共存，C程序员也清楚地了解面向对象可以与面向过程共存。因此我们可以暂时忽略这些评价，将面向数据设计视为一种和其他范式平等的，可以共存的重要工具。

回到2009年，那时硬件已经充分发展，准备好迎接开发方式的改变。然而理论上非常快的计算机却掣肘于忽视硬件的编程范式，当时那些游戏程序员的代码让引擎程序员见者落泪。后来时代变了，许多移动和桌面解决方案好像变得不那么依赖面向数据设计了，这倒不是因为设备的性能和优化稀释了代码的性能劣势，而是因为游戏的架构设计变得不那么严苛、复杂了。但展望未来，就连移动平台开发似乎也正转向3A级别，这意味着掌控系统复杂度、压榨硬件性能这些需求终将回归。

我们正生活在一个衣服口袋里就能装下多核机器的世界，因此学习如何在软件开发中避免串行是很重要的。不再依赖对象的消息传递、总是立即获得响应是面向数据编程的优势之一。如果你对数据流的理解胸有成竹，意味着你已踏出迈向GPGPU等其他计算方式的第一步，而它终将指引你完成开发游戏大作的壮举。对面向数据设计的需求只会不断增长。因为抽象和串行的思维将成为你竞争对手遭遇的瓶颈，而那些拥抱面向数据方法的人才能蓬勃发展。

## 数据至上 | It's all about the data

数据是我们仅有的东西了。

为创造用户体验，我们处理数据；
当我们打开文档，我们加载数据。

数据是你屏幕上显示的图像、手柄上按键发送的脉冲、让扬声器产生声波的起因、是你在游戏里得以升级、坏蛋获取你的位置并能向你开枪等等这一切的根源。

<p class="sidenote">指《索尼克》中摔跤时掉落一地的リング。</p>

数据是炸药爆炸之前所剩的时间，以及你摔落在尖刺上时丢掉金环的数量。

它是游戏结尾那美丽场景中每个粒子的位置和速度；而从硬盘里来到你生活中的这款游戏，也经历了从源代码到编译器、汇编到机器指令、最后成为磁头机械运动的漫漫长路。

没有数据，应用将一无是处。

没有图片的Photoshop，没有笔刷，没有图层，没有压感。
没有字符，没有字体，没有分页的Word。
没有事件的FL Studio。
没有源文件的Visual Studio。

所有一切被我们编写出来的应用程序，都是为了处理数据并输出数据存在。也许有的数据形式极度复杂、有的则简单到连文档都不用写，但归根结底，所有应用程序都需要并产生数据。如果有不需要正经数据的程序，那顶多算是玩具或者‘技术演示’罢了。

<p class="sidenote">哈佛（Harvard）架构中，指令和数据分处两个独立寻址空间；冯·诺伊曼（Von Neumann）架构则共用一个RAM。文中提到的Modified Harvard是目前计算机的主流架构，内存中指令和数据共存，CPU Cache中则分为指令缓存与数据缓存。</p>

指令也是数据。它们占据内存，占用带宽，可以进行转换、加载、保存和构造。开发者们会自然而然地认为指令和数据是割裂的。不过在旧一点的、保护性较低的硬件上，这二者几乎没有什么区别。尽管在现代硬件上，为保存可执行文件本身所预留的空间会受到保护，不会被损坏或修改，但这项创新目前还停留在“一项创新”这个阶段。目前的Modified Harvard Architecture依然仰赖同一个内存空间来存储数据和指令。因此，指令也是数据，是我们需要处理的东西。我们读取指令，将其化为实际行为。它们的数量、大小和频率都会产生影响。决定用哪些指令来解决一个问题的过程，便是优化。有了对数据的理解，我们就能“因材施教”；而通过了解运行指令产生的后果，我们可以确定哪些是必要的、哪些是冗余的、哪些有性能更好的替代品。

这几乎就是面向数据开发方法的基础了，只差最后一点：所有这些数据和转换，不管是字符串、图像还是指令，都必须基于某个设备进行。有时候这个设备是抽象的，比如一台虚拟机，我们不知道外部实际的硬件条件；有时候又很具体，像是自己的设备，CPU、GPU、内存和带宽都很明确。总之，数据不仅仅是“某数据”，而是“位于某地某硬件上的数据”。本质上讲，面向数据设计就是通过给结构良好的数据开发处理方式来设计软件的过程。而结构良好的标准则取决于目标硬件和在其上执行的数据变换的模式与种类。也许偶尔数据并没有很好地定义，也许偶尔硬件条件摸不清楚，但大多数时候，对硬件的了解总会给软件开发带来优势。

如果应用程序终将输出数据、所有输入都被表示为数据、所有的数据变换也有迹可循，那么软件开发的方法论便可奠基于这些原则之上；这些原则关乎对数据、对计算机会如何处理特定数量、频次和统计学特性的数据的理解。根植于此，我们就能建立起面向数据方法论的一套基本论点。

    施工中...