---
layout: wiki
wiki: SleepyBot
title: Database
order: 103
---

Database模块提供数据的提交和查询功能。

## Eat what

### 提交：吃的 {吃的}

提交一个选项到当前QQ群的吃饭清单。

### {*}吃什么！

从当前群里的吃饭清单中随机选取一个选项。

{% noteblock color:light In %}
年夜饭吃什么！
{% endnoteblock %}

{% noteblock color:dark Out %}
就去吃煎饼
{% endnoteblock %}

### {*}有什么吃的！

列出当前群里所有的吃饭选项。

<p class="smaller">可以不带感叹号。</p>

{% noteblock color:light In %}
这儿有什么吃的
{% endnoteblock %}

{% noteblock color:dark Out %}
我去看看！
1\. 汉堡王！
2\. 煎饼
3\. 牛肉面
{% endnoteblock %}

## Blog

### 提交：博客 {链接}

提交自己的博客链接，与QQ号绑定。

<p class="smaller">会解析http/Http开头的链接，之前的部分会被忽略</p>

### hexo d

获取自己的博客链接。

{% noteblock color:light In %}
hexo d
{% endnoteblock %}

{% noteblock color:dark Out %}
奥运会的博客已部署于https://fceek.github.io
<hr>
奥运会，你还没有记录在案的博客。
{% endnoteblock %}

## Miscellaneous

### {*}答案之书{\*}！

获取一个[答案之书](https://github.com/D1N910/answers-of-my-life)中的答案。

<p class="smaller">至于为什么每次答案之书都要Credit一下出处，当然是为了在出现傻逼答案的时候甩锅啦（</p>

{% noteblock color:light In %}
答案之书！
{% endnoteblock %}

{% noteblock color:dark Out %}
它说： 你必须弥补这个缺点
答案之书获取自 https://github.com/D1N910/answers-of-my-life
{% endnoteblock %}

### Wordle start

获取一个用来启动Wordle小游戏的单词列表。

{% noteblock color:light In %}
Wordle start
{% endnoteblock %}

{% noteblock color:dark Out %}
今天就从这些词开始吧！
socko
foram
muffs
snigs
erses
{% endnoteblock %}