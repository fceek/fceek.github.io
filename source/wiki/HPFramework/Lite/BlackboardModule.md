---
layout: wiki
wiki: HPFramework
title: BlackboardModule
order: 1005
---

黑板模块，在游戏中实现非持久性且方便的脚本间数据共享。

## Directions

在注册时会默认提供一块`id`为default的黑板。

## API - Module

### GetOrCreateBoard(string id) : Blackboard

获得一块指定id的黑板，如果不存在则创建一块新的黑板。

{% noteblock color:light Param %}
*id* : 黑板名称，一个可望文生义的、独特的字符串。
{% endnoteblock %}

{% noteblock color:dark Return %}
一块具有指定id的黑板。
{% endnoteblock %}

{% noteblock child:codeblock color:green %}
```C#
BlackboardModule bb = App.Modules.Get<BlackboardModule>();

// 获取默认黑板
Blackboard defaultBb = bb.GetOrCreateBoard("default");
// 创建（或是获取别的脚本创建的）自定义黑板
Blackboard customBb = bb.GetOrCreateBoard("bankBb");
```
{% endnoteblock %}

## API - Blackboard

### Set(string id, object v)

在黑板上设置一条数据。

{% noteblock color:light Param %}
*id* : 数据名称，一个可望文生义的、独特的字符串；
*v* : 此名称下存储的数据，可以是任意object。
{% endnoteblock %}

### Get\<T\>(string id, T fallback) : T

从黑板上读取一条数据。

{% noteblock color:light Param %}
*T* : 要查询的数据类型；
*id* : 数据名称，一个可望文生义的、独特的字符串；
*fallback* : 黑板上没有查询到这条数据时所返回的默认值。
{% endnoteblock %}

{% noteblock color:dark Return %}
id所对应的数据，如果没有则返回fallback的值。
{% endnoteblock %}

{% noteblock child:codeblock color:green %}
```C#
BlackboardModule bb = App.Modules.Get<BlackboardModule>();
Blackboard bankBb = bb.GetOrCreateBoard("bankBb");

// 写上自定义数据（可以是任意类型）
bankBb.Set("Mulan Garden", 175);

// 只要读取的时候使用对应的类型即可，在另一脚本中
bankBb.Get<int>("Mulan Garden", -1); // 175
bankBb.Get<int>("Preston Park", -1); // -1
```
{% endnoteblock %}