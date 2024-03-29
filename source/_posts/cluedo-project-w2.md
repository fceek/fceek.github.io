---
title: Cluedo Project Tutorial/DevLog - Week 2
date: 2021-02-16 03:54:30
categories: [DevLog, Cluedo]
tags: [Coursework, Python, Software Engineering]
---

Software Engineering Group Project, Cluedo, Week 2 post.
<!-- more -->

{% noteblock color:blue ℹ 插播一下，我在网站更新了Reference List + 功能，就在右上角↗%}
**2021.11更新：新网站的Ref+入口在左侧导航栏。**
里面会包括我提到过的链接，Canvas上一些文件的直接下载地址（大概会比去Canvas里翻方便一些？）和其他的一些有用链接。
{% endnoteblock %}

<br>

>这周终于要写代码了。<br>好像也没必要设deadline，毕竟真干起活来激发潜能一周能啃八周的量。<br>比如上周大概半小时不到的内容，放在这周开写之前弄一下就行了（大概？）。


## Intro


第一周的热身结束了，考虑到下周一必须要有实际产出，这篇文章又因为我个人原因拖了两天没及时发出来，之后的几天和这个周末可能会比较赶？不过我会在“还是得看需求文档”的前提下尽量把这周所需要的底层设计写的详细一点，这样大家拿到手之后，如果对游戏规则熟的话基本只需要完形填空。除此之外我还会简单理一下整个项目的时间线。

如果每周的东西没人做我之后会自己补，稍微拖一拖其实无所谓（毕竟我自己也狂拖）。但这个项目并不是只有一个阶段，各个阶段之间还有继承和依赖关系，做到后面发现缺东西可能就会提前进入修补程序，要是一直拖到我提前把你的活儿补了就只能痛失这个份额了。总结起来就是，拖延症随便拖，但是只能拖到我忍不住把你的活干了之前😅。


## General Planning

### Timeline

在文章的最开始，我想先算一下时间，这样比较方便给出一个整体的时间规划（紧迫感拉满）。

这周是整个学期的第四周，整个作业的DDL在十一周/四月30号，加上中间的复活节假期，实际上留给我们的时间是正好十周。
从这周开始有的Seminars理论上来说是要给出Demo展示进度的，这周被Git Workshop顶掉了所以不用，下一周的正常Seminar就得拿东西出来了，因此第一个开发周期只截至下周一。剩下的则是两周一个周期，最后留下一周多用来补文档和应对突发情况。


<a href = "timeline.jpg" target = "_blank"><img class="primary" src="timeline.jpg"></a>
<figcaption class="primary">Estimated Timeline (长图点大)</figcaption>

### Milestones

于是可以设置的Milestone一共有四个半。那半个是这周需要五天速成的简单难度目标，剩下四个是普通难度，如果做GUI那个周期发现库有点难上手可能那个周期会变成困难难度，这时候就可以从预留的一周多时间里抽几天过来用。暂定的Milestones大概这样：

|M1|M2|M3|M4|M5|
|---|---|---|---|---|
|命令行|命令行|GUI|GUI|外部工具|
|核心机制|AI，完整游戏|残局模式，残局编辑器|完整游戏|Debug，优化，Release|
|玩家进行回合，在版图里行动，提出怀疑，下达指控并取胜/淘汰|LogBook，菜单等外部功能，玩家与AI玩家进行游戏|由外部文件导入残局，AI玩家模拟对局，编辑器自定义生成残局文件|实现GUI，版图/角色自定义|系统测试，增删改查，V1.0|

{% noteblock color:yellow %}
**⚠** 这个表我是按照之前读需求文档，和自己打的两三把Steam版Cluedo的记忆写出来的，有可能会缺功能，发现有缺漏请务必告诉我。
{% endnoteblock %}

## Sprint Cycle 1

### WalkThrough

这个版本的显式流程，大概就是最后成品进游戏需要达到的效果。

- 指定人数开始游戏
- 每个人依次进行回合
  - 显示此玩家的手牌
  - 扔骰子，得出本回合玩家可以前往的房间
  - 玩家选择前往哪个房间
  - 提出怀疑
    - 其他玩家展示手牌
    - 如果有多张手牌可展示，让该玩家选择
  - 询问玩家是否提出指控
    - 指控失败则淘汰玩家
  - 进入下个玩家的回合
- 某个玩家取得胜利或收到退出指令


### Class List

{% noteblock color:yellow %}
**⚠** 这部分内容同样不是最终版，要达成设计流程肯定还要加点什么，具体写代码的时候得随机应变。稍微有点挑战性才有趣（？
{% endnoteblock %}


<a href = "class-diagram.jpg" target = "_blank"><img class="primary" src="class-diagram.jpg"></a>
<figcaption class="primary">UML Class Diagram</figcaption>

#### Cluedo

游戏的主入口，目前只需要接收一个玩家输入的人数，然后以这个人数为参数新建一局 `CluedoGame` 就行。

#### CluedoGame

一局游戏的本体，创建后应进行的初始化：

- 根据玩家人数填充 `Players`
- 将 `NextPlayer` 设置为Player 1
- 获取所有的卡片信息填充到 `Cards`
  - 这里我觉得可以从一个单独的结构体甚至是外部文件导入这些卡片的信息，而不推荐直接写在这个Class的代码里
- 从每个种类的卡里选一张作为正确答案
- 建立 `GameBoard`
- 将所有的玩家放置在 `GameBoard` 起始点
- 给玩家发放手牌
- 开始第一个回合

进行回合的方法为 `ProcessTurn()`，在这个方法中可能被调用的方法有：

- `DiceRoll()`
  - 掷骰子
- `Suspect()`
  - 提出怀疑
- `Accuse()`
  - 提出指控

...等，具体逻辑参考上一节的显式流程，

另外需要一个方法 `GetPlayerInput()` 用于接收玩家输入的指令。

#### Player

玩家，里面存玩家的角色名（目前就用Player 1、Player 2这样吧），手上的牌和目前在 `GameBoard` 上的坐标 `Coordinate`。

#### Card

游戏中要用到的卡牌，存卡牌的类型（人物/武器/房间），具体描述文字和是否被选为正确答案。

关于正确答案我觉得可以用 `IsAnswer` 和 `MakeAnswer()` 将它放到 `Card` 类里面处理，也可以在 `CluedoGame` 里添加一个答案属性用来存，存疑。

#### GameBoard

游戏版图，关于版图信息本身像 `Card` 一样也应该是分离出来比较好，建立版图的时候从里面读。
属性具体有一组 `Room` ，是版图里的房间。几个方法分别用来移动玩家和检查玩家行走n步能到达的房间列表。

这部分可能是整个项目里唯一要用到算法的地方，因为走路的时候要绕开别的玩家的棋子，具体实现上可以增加一个 `Occupied` 属性来存有人的格子，或者建立从 `GameBoard` 到 `CluedoGame` 的反向索引来获取 `Players` 。解决办法随便一想就有好几种，这也是需要纠结的源头，写的时候看怎么方便怎么来吧。

#### Room

房间，有名字和入口坐标。


## 这周的主线任务

首先我觉得读一下代码标准很有必要：

<a class="doc-link" href = "https://google.github.io/styleguide/pyguide.html">Python Style Guide</a>

我的建议是每个人都自己写一份自己版本的代码出来，因为目前版本的内容不多，这么高耦合的几个Class如果分几个人来写反而会更麻烦。然后关于处理上有差异的点就可以拿出来比较一下优劣什么的。

当然作为Group Work合作完成也完全没问题，解决高耦合对接不上的问题其中一个方法是，大家连麦/Screen Share一起写，就和Kingsley在课上推荐的Pair Coding差不多意思，大家要是想的话可以自己商量商量分工什么的。

如果事情比较顺利我就去写这部分的单元测试了，这样周末我就可以把提交上来的代码跑跑看。如果不太顺利这周就先不搞单元测试，集中火力先胡一个下周一能给Kingsley看的Demo再说。
