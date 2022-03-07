---
layout: wiki
wiki: HPFramework
title: UIModule
order: 1006
---

UI模块，用于控制UI窗口的显示与销毁。

## Directions

相较于框架原版，这个模块被极度简化了，没有UI分层、显示顺序、自动绑定和缓存等特性，希望在这个项目里Minimal版本够用。

模块注册时会基于`Resources/Defaults/MainCanvas`创建主Canvas，之后的所有UI内容都会加载在这个Canvas上，此Canvas的顺序为1，会默认显示在最前。

考虑到这个项目应该不会有同时显示多个同类型窗口的需求，模块在一些地方使用了唯一名称判断，因此UI组件不能重名，同一组件不能同时显示多个。

## API

此模块提供的方法为静态，可以直接使用类名调用。

### ShowUI(GameObject go) : GameObject

加载并显示UI Prefab。

{% noteblock color:light Param %}
*go* : 一个预制好的UI组件。
{% endnoteblock %}

{% noteblock color:dark Return %}
返回生成的GameObject，方便使用*GetComponent*进行操作。
{% endnoteblock %}

### DestroyUI(string id)

销毁一个UI组件。

{% noteblock color:light Param %}
*id* : 要销毁的UI组件的名称，一般来说会是Prefab的名字。
{% endnoteblock %}

### DestroyUI(GameObject go)

销毁一个UI组件。

{% noteblock color:light Param %}
*go* : 要销毁的UI组件。
{% endnoteblock %}

{% noteblock child:codeblock color:green %}
```C#
private GameObject purchaseWindow;
// 在Inspector中设置了purchaseWindow到预制的组件PurchaseWindow.prefab的reference

// 显示这个窗口
GameObject window = UIModule.ShowUI(purchaseWindow);

// 关闭这个窗口
UIModule.DestroyUI(window);
// 或
UIModule.DestroyUI("PurchaseWindow");
```
{% endnoteblock %}