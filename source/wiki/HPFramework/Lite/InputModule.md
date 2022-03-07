---
layout: wiki
wiki: HPFramework
title: InputModule
order: 1003
---

输入模块，由于本项目交互基本是纯点击，且没有需要持续生效的通用按键绑定，这个模块其实不是很必要。

## API

### BindAction(string inputName, Action\<InputAction.CallbackContext\> action)

将一个按键绑定到监听者。

{% noteblock color:light Param %}
*inputName* : 事件名称，形如“设备/操作”，具体参见[官方文档](https://docs.unity3d.com/Packages/com.unity.inputsystem@1.3/api/UnityEngine.InputSystem.InputActionAsset.html#UnityEngine_InputSystem_InputActionAsset_FindAction_System_String_System_Boolean_)；
*action* : 事件的监听者，接收输入参数的方法或Lambda。
{% endnoteblock %}

{% noteblock child:codeblock color:green %}
```C#
InputModule i = App.Modules.Get<InputModule>();

// 使用一个方法监听鼠标滚轮。
i.BindAction("Mouse/Scroll", MouseScrollHandler);

private void MouseScroolHandler(InputAction.CallbackContext ctx) {
    // ...
}

// 使用Lambda监听键盘‘任意键’。
i.BindAction("Keyboard/Anykey", ctx => {
    // ...
});
```
{% endnoteblock %}