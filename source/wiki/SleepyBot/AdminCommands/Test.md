---
layout: wiki
wiki: SleepyBot
title: Test
order: 201
---

Test模块提供一系列开发者指令，方便在不登陆服务器终端的情况下进行一些操作。
此模块中所有指令只有开发者QQ（参见Deploy/DevId）发送才有效，同时只有开发者QQ发起的加群邀请Bot才会同意。

## Tests

### Test:DBConnection

测试机器人到Redis数据库的连接情况。

{% noteblock color:light In %}
Test:DBConnection
{% endnoteblock %}

{% noteblock color:dark Out %}
已连接至云端数据库。
<hr>
云端数据库连接失败。
{% endnoteblock %}

### Test:YabiAPI

测试机器人到[亚逼日历](https://yabi.fizzli.dev/home)API的连接情况。

{% noteblock color:cyan %}
**!TODO** 目前缺少消息反馈，只能在命令行查看测试结果
{% endnoteblock %}

## Crawlers

### Test:GCoreCrawler PageRange={页数}

爬取并缓存机核电台前{页数}页的电台链接。

{% noteblock color:light In %}
Test:GCoreCrawler PageRange=5
{% endnoteblock %}

{% noteblock color:dark Out %}
This may take a while...
finished
{% endnoteblock %}

### Test:GCoreCrawler CacheInfo

爬取所有已缓存链接的机核电台的标题与简介。

{% noteblock color:cyan %}
**!TODO** 目前缺少消息反馈，只能在命令行查看测试结果
{% endnoteblock %}

