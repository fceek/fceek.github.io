---
title: Cluedo Project Tutorial - Week 1
date: 2021-02-10 21:15:50
tags:
---

Software Engineering Group Project, Cluedo, Week 1 post.
<!-- more -->


>首先抱歉把大家都默认成没什么基础（或者说项目经验）的程序员练习生。<br>Special apologise to Link, too lazy to write in both Chinese and English. So when Link you are free enough you can skip this and summon me to your room.



## Intro

随着开学之后时间的推移，Software Engineering的大作业也被迫提上了日程，这篇文章或者如果之后还有东西写做成系列的话，我想把它做成一个*QuickStart*之类的东西。因为Python项目这方面我也是刚学（从昨天晚上八点半开始），我想如果直接把整个学习过程输出成一个总结性的报告，可以让你们在接手项目的时候减少很多浪费的时间。毕竟这些玩意儿的过程和背后的原理，实际用起来并不必须了解，如果我能直接总结给你们现成的命令应该没啥问题。

顺便附个免责声明（毕竟也才学了一天，理解万岁）：本文使用的工具及其版本可能会在之后由于项目需要发生改动，对此我也没啥办法🙄。

首先明确一下现阶段的总目标：完成一个**命令行版**（没有图形界面）**Cluedo游戏原型**（不考虑用户体验，只考虑程序逻辑）。

这周的小目标则是，每个人都配置好基本Python开发环境，了解一下目前的项目结构，配置好Git并实现一次合作编辑。

## Python环境

### 本体

<a class="doc-link" href = "https://docs.python.org/3.8/">Documentation</a>

Python版本使用3.8.7，理由是3.9还未进入稳定期，在稳定版本里我大胆猜想越新越好就选了。

下载链接：[Windows(x64)](https://www.python.org/ftp/python/3.8.7/python-3.8.7-amd64.exe) , [Mac OS X 10.9+](https://www.python.org/ftp/python/3.8.7/python-3.8.7-macosx10.9.pkg)

Python的命令随系统的不同会不一样，`py`是 *Windows Python Launcher* 的命令，可以通过配置`py.ini`来启动任意指定版本的Python。 **[- Reference](https://stackoverflow.com/a/21257622)**

其他系统/版本下可能是 `python` `python3` 之类的命令，试一下就行，之后可以自行代换。
系统里如果存在多个版本的python，使用 `-0` 选项可以查看所有已安装的版本，`--version` 查看当前使用的版本。

<figcaption>Example in WindowsTerminal, pwsh6</figcaption> 
<a href = "python-cmd.jpg" target = "_blank"><img class = "primary" src = "python-cmd.jpg"/></a>  

以上讨论的都是在命令行环境中的情况，用于集成/测试，在开发过程中有了VSCode或者PyCharm这样的IDE帮助，Python版本反倒不是什么问题。

<figcaption>Choosing Python version, VSCode + Pylance</figcaption>
<a href = "vscode-pylance.png" target = "_blank"><img class="primary" src="vscode-pylance.png" /></a>

### pip

<a class="doc-link" href = "https://pip.pypa.io/en/stable/">Documentation</a>

除了Python本体之外，我们还需要 `pip` 工具来安装Python的其他组件，一般来说Python安装的时候会附带，同理使用 `pip --version` 可以查看其版本，目前的最新版本是21.0.1。

{% noteblock color:orange ⚠&nbspHOTFIX&nbsp1202 %}
pip命令可能需要在前面加Python模块命令变成像 `py -m pip...` 一样才能正确运行。
以及几乎不可能不附带pip，可以直接upgrade。
{% endnoteblock %}


如果没有 **[- Reference](https://pip.pypa.io/en/stable/installing/)**
```
install:
    curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
    py get-pip.py
upgrade:
    py -m pip install -U pip
```

### PyTest

<a class="doc-link" href = "https://docs.pytest.org/en/stable/">Documentation</a>

最后一项是PyTest，它是Python的单元测试库，相当于Year 1时Further Programming里用的Java单元测试库Junit。
目前还不需要了解这玩意儿怎么用，我昨晚已经写了个日志记录功能，附了一个Hello World测试玩儿（这样到最后我们可以统计出来一共跑了多少次测试，Just for fun）。

虽然这两周大概用不到PyTest，但这个功能正好可以用来检查这周的任务😟。

```
pip install -U pytest
pytest --version
```

## Git

第二部分是版本控制，小打小闹用GitHub就完事了。

### Git Local

要进行本地的Git版本控制，硬核程序员很多都直接使用Git Bash，即直接在命令行中与Git进行交互。
但现阶段我推荐使用有GUI的Git工具，例如 [SourceTree](https://www.sourcetreeapp.com/) 或 [GitKraken](https://www.gitkraken.com/) 。这样可以免去记住Git命令、了解Git原理、不小心输错命令之类的麻烦（有些甚至是毁灭性的），当然如果你想要了解可以去看我很久之前发的这篇知乎专栏：[Missing Semester (六)：Version Control (Git)](https://zhuanlan.zhihu.com/p/139820055) ，结合[Git Bash的文档](https://git-scm.com/doc)就不用上面提到的工具了。

{% noteblock color:orange ⚠&nbspHOTFIX&nbsp1202 %}
GitKraken需要验证学生邮箱才能免费使用，具体流程是给GitHub帐号绑定Sussex邮箱之后申请GitHub Education，之后按GitKraken官网提示。GitHub Education验证流程较长，一般需要等待一周，早申早快乐。
{% endnoteblock %}

### Git Remote & Collab

远端仓库托管在大家最爱的GitHub上，要进行协作首先每个人要创建自己的GitHub帐号。这篇文章的页面最下方就有到我GitHub主页的链接👇。

项目的Git仓库（Repository）我已经建好了，并且做了基本框架，链接：

<a class="doc-link" href = "https://github.com/fceek/Cluedo-SE21">Cluedo-SE21, GitHub</a>

我选择的协作方式被称为 [Forking Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/forking-workflow) ，简单来说就是每个人复制一份仓库到自己的账号上，这样自己可以随便进行实验和改动而不用考虑主仓库的安危，在一个新功能/特性完成后，通过创建Pull Request的方式请求将自己更新的内容合并到主仓库去。在[这篇文章](https://www.atlassian.com/git/tutorials/making-a-pull-request)的后半部分有关于这种流程的一个更详细的例子。

针对我们的项目，流程大概是：
- 进入上面的仓库链接
- 点击右上角三个按钮（Watch/Star/Fork）中的 `Fork`
  - 长这样 <img src="fork.jpg">
  - 这里的 `fork` 大概就是跨帐号的复制，同时也等于创建了一个分支
- 在本地使用Git工具将自己账号上的同名仓库 `Clone` 到本地
  - `clone` 也是复制，但指的是云端到本地的复制

<figcaption>Set your GitHub account before cloning is preferred, SourceTree</figcaption>
<a href = "sourcetree-remote-account.png" target = "_blank"><img class="primary" src="sourcetree-remote-account.png"/></a>

- 在本地用IDE/Shell对文件进行修改
  - 一般推荐使用 `Branch` 针对每个Feature单独分支
- 修改完毕之后使用 `Commit` 进行提交
  - 这会将 **你的仓库** **当前分支** **在本地** 的文件状态向前推进一个版本
- 通过 `Push` 将提交同步到远端，即GitHub服务器上的仓库
- 回到GitHub网站，这时网站会自动提示你，相较于主仓库，你的库领先了一/几个版本，从而可以提出Pull Request。
  - <img src="pull-request-auto.jpg">
  - 如果没有提示点上面一栏的Pull requests - New pull request也可以手动
  - 你甚至可以给别的fork了主仓库的人提出Pull request，从而将项目完美的树状结构拧成麻花（并没有说禁止这么做的意思）
- 在主仓库所有者（也就是我）检查了代码并通过之后，我们就成功的完成了一次协作。


## 项目结构与其他说明

参见项目里的Readme文件，或[在线查看](https://github.com/fceek/Cluedo-SE21/blob/master/README.md) 。
里面写的比较简略（因为我懒），如果对每个文件有疑问可以随时群里说。

{% note color:yellow ⚠&nbsp;项目中的Makefile文件是针对Windows环境下的nmake工具，以及batch语言编写的几个快捷方式/小工具，如果你使用Linux或OSX，再或者Windows下没有安装nmake工具，暂时无法享受这条捷径。%}


## 这周的主线任务

配置完成环境及本地仓库之后，读一下README

1. 跑一次单元测试，这应当会生成一个日志文件
2. 在 `/docs/MissionAccomplished.md` 中起一新行，随便写点什么
3. 提交以上的改动，发起Pull Request将其更新到主仓库