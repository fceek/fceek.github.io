---
layout: wiki
wiki: SleepyBot
title: Special
order: 104
---

这里是暂时没想好怎么归类的命令

## Commands

### hexo s

只是会返回一句 `本地Hexo项目的默认地址：http://localhost:4000` 而已。

### 亚逼日历！ {不要介绍|短点介绍|最近|?条}！

返回[亚逼日历](https://yabi.fizzli.dev/home)的最新事件数据。

- 不要介绍：不会显示事件详情；
- 短点介绍：事件详情只显示40个字符，默认是80个；
- 最近：只显示最近的一个事件记录；
- ?条：选择显示1-6条最近的事件记录。

如果不用任何选项，默认显示5条。

{% noteblock color:light In %}
亚逼日历！不要介绍 3条！
{% endnoteblock %}

{% noteblock color:dark Out %}
Steam 春节特卖
1月27日 16:00 - 2月3日 16:00

崎山蒼志 全长专辑 Face To Time Case
2月2日

milet 2nd full ablum Visions
2月2日
{% endnoteblock %}

### {*}为什么{\*}

机器人会复读所有带为什么的发言，并且在最后加上一个感叹号来强化你疑问的语气！

<p class="smaller">其实英文的Why也在侦测范围内，只是从来没有人触发过。</p>

{% noteblock color:light In %}
你妈的，为什么
{% endnoteblock %}

{% noteblock color:dark Out %}
你妈的，为什么！
{% endnoteblock %}