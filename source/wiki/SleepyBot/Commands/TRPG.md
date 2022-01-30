---
layout: wiki
wiki: SleepyBot
title: TRPG
order: 101
---

TRPG模块提供跑团相关的功能。

## Roll Dice

### roll {骰子个数}d{骰子面数}

扔出1-50个骰子，骰子至少有两个面（也就是至少是个硬币）。

<p class="smaller">指令里用Roll和roll，D和d都可以。<br>
如果在QQ群里使用，机器人会指明这次是谁扔的骰子。</p>

{% noteblock color:light In %}
roll 4d17
{% endnoteblock %}

{% noteblock color:dark Out %}
4, 14, 6, 8.
一共32点.
{% endnoteblock %}
