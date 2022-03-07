---
layout: wiki
wiki: HPFramework
title: SaveModule
order: 1004
---

存档模块，在Unity默认存档位置维护一个本地文件，用于游戏数据的持久性存储。

## Directions

为了提高存档性能，游戏过程中存档数据在内存中进行缓存，仅按需进行文件操作，因此退出游戏前需要使用`WriteSaveFile()`写入硬盘确保数据的持久性。

字符`|`为保留字，用于存档数据的分隔，请不要在存档中使用这一字符。

默认存档目录Windows下为`<user>\AppData\LocalLow\DefaultCompany\PropertyTycoon\saves`，Mac下为`~/Library/Application Support/DefaultCompany/PropertyTycoon/saves`。在最后Build前应该会把DefaultCompany改掉。

因为写入文本文件的关系，所有数据均为string类型，请在使用前进行转换。

## API

此模块提供的方法为静态，可以直接使用类名调用。

### CreateSaveFile(bool overwrite = false)

创建新的存档文件。因`SaveModule`在注册时会自动检测并生成存档文件，一般情况下没有使用此方法的必要。

{% noteblock color:light Param %}
*overwrite* : 是否覆盖原来的存档文件（如果存在）。
{% endnoteblock %}

## Read(string key) : string

从**内存**中读取一个存档条目。

{% noteblock color:light Param %}
*key* : 要读取的存档条目的key。
{% endnoteblock %}

{% noteblock color:dark Return %}
查询key所对应的存档数据，如果不存在则返回空字符串。
{% endnoteblock %}

## Save(string key, string value)

向**内存**中写入一个存档条目。

{% noteblock color:light Param %}
*key* : 要写入的存档条目的key。
*value* : 写入此条目的数据值。
{% endnoteblock %}

{% noteblock child:codeblock color:green %}
```C#
SaveModule.Save("GlobalVolume", "45");
SaveModule.Read("GlobalVolume"); // "45"
```
{% endnoteblock %}

## WriteSaveFile()

将内存中的存档数据写入存档文件，使目前的数据持久性存储。

## ReadSaveFile()

从存档文件中加载存档数据到内存。
这个方法会在存档模块被注册时自动调用。

{% noteblock color:light Param %}
*key* : 要写入的存档条目的key。
*value* : 写入此条目的数据值。
{% endnoteblock %}

{% noteblock child:codeblock color:green %}
```C#
SaveModule.Save("GlobalVolume", "45");
SaveModule.WriteSaveFile();
// 退出游戏
// 重新启动游戏，存档模块注册时会自动读取一次，因此不需要再调用ReadSaveFile()
SaveModule.Read("GlobalVolume"); // "45"
```
{% endnoteblock %}