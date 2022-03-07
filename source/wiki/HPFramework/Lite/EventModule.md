---
layout: wiki
wiki: HPFramework
title: EventModule
order: 1002
---

事件模块，跨脚本监听事件并传递事件参数。

## API

### Listen(string id, Action\<object, object\> action)

监听一个事件。

{% noteblock color:light Param %}
*id* : 事件名称，一个可望文生义的、独特的字符串；
*action* : 事件的监听者，接收事件发送者、传入数据两个参数的方法或Lambda。
{% endnoteblock %}

{% noteblock child:codeblock color:green %}
```C#
EventModule e = App.Modules.Get<EventModule>();

// 使用一个方法监听OnGameOver事件。
e.Listen("OnGameOver", OnGameOverHandler);

private void OnGameOverHandler(object sender, object data) {
    // ...
}

// 使用Lambda监听OnBankrupted事件
e.Listen("OnBankrupted", (sender, data) => {
    // ...
})
```
{% endnoteblock %}

### Invoke(string id, object args = null)

触发一个事件。

{% noteblock color:light Param %}
*id* : 事件名称，一个可望文生义的、独特的字符串；
*args* : 事件参数/数据（可选），多个参数应构造成一个object发送。
{% endnoteblock %}

{% noteblock child:codeblock color:green %}
```C#
EventModule e = App.Modules.Get<EventModule>();

// 触发不带参数的OnGameStart事件
e.Invoke("OnGameStart");

// 触发带参数的OnBankrupted事件
e.Invoke("OnBankrupted", "Player 5 as Cat");
```
{% endnoteblock %}

### Remove(string id, Action\<object, object\> action)

移除对一个事件的监听。

{% noteblock color:light Param %}
*id* : 事件名称，一个可望文生义的、独特的字符串；
*action* : 之前设置的监听者；
{% endnoteblock %}

{% noteblock child:codeblock color:green %}
```C#
EventModule e = App.Modules.Get<EventModule>();

// 使用一个方法监听OnGameOver事件。
e.Listen("OnGameOver", OnGameOverHandler);

private void OnGameOverHandler(object sender, object data) {
    // ...
}

e.Remove("OnGameOver", OnGameOverHandler); // 现在触发时不会再调用OnGameOverHandler。
```
{% endnoteblock %}