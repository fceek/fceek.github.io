---
title: Cluedo Project Tutorial/DevLog - Week 2+
date: 2021-2-22 16:42:13
tags:
---

>纸上得来终觉浅，绝知此事要躬行 / <br>Software Engineering Group Project, Cluedo, Week 2 post.

<!-- more -->

## Intro

大概知道为什么架构师和设计文档编写一般需要有经验的程序员来担当，而实际上写那些模块的都是实习生了。如果没有足够的项目积累，只凭空想做出来的设计大概率是不能100%落实的。今天写程序的时候深切地体会到这一点，也就是说，这周实际上产出的程序，和上周我在文章里预想的并不一样。

这次的篇幅会很短，毕竟只是对上周内容的补充，如果真和上周一样长怕不是等于上周白写了。主要就说一下更新Fork仓库，至于代码设计上的改动，代码文档里应该有写。


## Syncing

如果你之前已经Fork了[主仓库](https://github.com/fceek/Cluedo-SE21)，截至现在这个时间点，主仓库已经有了新的提交。由于Fork本质上创建了一个独立的新仓库，这些新的提交并不会被同步到你Fork过去的仓库上，为了能继续在同一个代码基础上施工，就需要一些设置，把主仓库的新提交同步到自己的仓库上。

这部分因为我自己没什么实践的机会，只能说是提供几个参考文档，然后再基于这些文档搞点猜想。如果有人先试出来稳定的流程了可以分享一下。

### With Bash

我就直接放个代码然后解释两句，实际上用Git Bash的不多（反正我推荐的是用客户端），但是要看代码了解这个流程，才好猜在客户端里怎么操作。。 **[- Reference](https://docs.pytest.org/en/stable/)**

```
git remote add upstream https://github.com/fceek/Cluedo-SE21.git
    # 将主仓库添加到remote里，命名为upstream
git fetch upstream
    # 从刚刚添加的upstream里把仓库拖到本地
git checkout [YOUR BRANCH HERE]
    # 检出一个新的本地分支（如果是master就是切换到本地主分支，起个名儿就是创建新分支）
git merge upstream/Chen
    # 把拖下来的upstream里的分支Chen（因为代码更新在这个分支了）归并到刚检出的分支里

=== OR ===

git checkout [YOUR BRANCH HERE]
    # 检出新的本地分支
git pull https://github.com/fceek/Cluedo-SE21.git Chen
    # 直接从URL把我的分支拉取过来，这会自动进行一次merge操作
COMMIT AND PUSH
```

### With Client

这里只提供一个使用SourceTree进行以上流程的猜想，不一定对

<a href = "add-remote.jpg" target = "_blank" ><img class="primary" src="add-remote.jpg"></a>
<figcaption class="primary">Add to remote, SourceTree</figcaption>

<br>

<a href = "fetch-from-upstream.png" target = "_blank"><img class="primary" src="fetch-from-upstream.png"></a>
<figcaption class="primary">Fetch from newly added remote, SourceTree</figcaption>

使用`Fetch`本质上等于把下面的`Pull`操作拆成两步，先下载文件但不和本地的Branch合并，之后再手动`Merge`

=== OR ===

<a href = "pull-from-upstream.png" target = "_blank"><img class="primary" src="pull-from-upstream.png"></a>
<figcaption class="primary">Pull from newly added remote, SourceTree</figcaption>

直接拉取需要注意选择**从**哪个Branch拉取，和拉取**到**哪个Branch，一步到位


## Other

代码任务大概就是尽可能补完 `/dev/cluedo_dev.py` 里的代码了。
因为我只写了框架为了方便和不报错，有些地方我写的比较妥协，所以和之前老师给的那种完形填空不一样的是，如果觉得必要我写的东西你也随便改😉。

总结一下有三个关键点：

- 从外部文件中读取游戏版图，卡组等
  - 后面可能也会加人物定制，可以未雨绸缪一下
  - 我推荐用JSON或者XML，一是主流，二是Python对它们有支持
- 版图的数据结构和游戏中角色移动的路径计算
- `process_accuse()` 中对其余玩家手牌的轮询

解决这三点别的都是切菜，其他具体内容参考代码内文档。