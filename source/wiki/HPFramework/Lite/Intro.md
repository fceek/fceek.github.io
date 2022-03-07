---
layout: wiki
wiki: HPFramework
title: Intro
order: 1000
---

HPFramework Lite版是嵌入ReImagined-Monopoly项目的定制、简化版框架。

## Architecture

为了尽量简化及减少耦合，框架仅由一个主入口`App`、模块分发系统`Modules`和一系列单文件模块构成。
所有模块均继承自`GameModule`抽象类，需实现`OnRegister()`和`OnUnregister()`方法，会在模块注册及销毁时自动调用。

## Life Cycle

在场景加载前（具体为`SubsystemRegistration`时），App中的`Start()`方法会被调用。在其中初始化`Modules`，然后使用`Modules`依次注册所有模块。最后会输出Debug信息表示启动完成。