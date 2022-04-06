---
layout: wiki
wiki: SleepyBot
title: TRPG
order: 101
---

TRPG模块提供跑团相关的功能。

## Roll Dice

### roll {骰子个数}d{骰子面数}(+更多骰子)

扔出1-50个骰子，骰子至少有两个面（也就是至少是个硬币）。
可以用+的方式在后面接任意多种类的骰子。

<p class="smaller">指令里用Roll和roll，D和d都可以。<br>
如果在QQ群里使用，机器人会指明这次是谁扔的骰子。</p>

{% noteblock color:light In %}
roll 4d17
<hr>
roll 2d3+3d4+4D5
{% endnoteblock %}

{% noteblock color:dark Out %}
掷出了4个17面骰： 11, 14, 17, 6. 共48点.
总计48点。
<hr>
掷出了2个3面骰： 3, 2. 共5点.<br>
掷出了3个4面骰： 4, 3, 1. 共8点.<br>
掷出了4个5面骰： 1, 1, 1, 3. 共6点.<br>
总计19点。
{% endnoteblock %}
