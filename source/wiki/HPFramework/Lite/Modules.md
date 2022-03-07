---
layout: wiki
wiki: HPFramework
title: Modules
order: 1001
---

`Modules`为原框架中`ModuleDispatcher`的简化版，默认所有模块均为`MonoBehaviour`进行处理，即给予每个模块一个单独的GameObject挂载在`DontDestoryOnLoad`下。

## API

### Get\<T\>() : T

获取类型为`T`的模块。

{% noteblock color:light Param %}
*T* : 想要获取的模块类，需要继承自`GameModule`。
{% endnoteblock %}

{% noteblock color:dark Return %}
类型为 *T* 的模块实例。
{% endnoteblock %}

{% noteblock child:codeblock color:green %}
```C#
// 获取游戏的存档模块并存为变量save。
SaveModule save = App.Modules.Get<SaveModule>(); 
```
{% endnoteblock %}

## Dev

{% noteblock color:yellow %}
⚠ 如果你在开发中遇到了觉得需要使用以下方法的情况，请先找我商量。
{% endnoteblock %}

### Register\<T\>()

注册类型为`T`的模块。

### Unregister\<T\>()

销毁类型为`T`的模块。