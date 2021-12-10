---
layout: wiki
wiki: Stellar-FC
title: Customisation List 
---

> 记录一下目前为止对主题的修改，方便之后查阅或定位问题。

## 全局

### 禁用Dark Mode

不喜欢黑色主题，在主题 `config.yml` 结尾处修改了 `darkmode: false` 。

### 添加自定义css文件

位于主题 `source/css/_fceek/` 下。

## 媒体

### 图片呈现

使用 `<img class="primary">` 显示限宽600px，带阴影和Hover效果的图片。
使用 `<figcaption class="primary">` 在图片下方显示图注。

{% codeblock 示例 lang:html %}
<a href="index/logo7.jpg" target="_blank"><img class="primary" src="index/logo7.jpg"></a>
<figcaption class="primary"> Just a logo</figcaption>
{% endcodeblock %}

<hr>

<a href="index/logo7.jpg" target="_blank"><img class="primary" src="index/logo7.jpg"></a>
<figcaption class="primary"> Just a logo</figcaption>

## 行文

使用 `<p class="sidenote">` 为其下方的一段正文添加边注。
`<p class="sidenote tldr">` 是另一种样式的边注，用于总结或Paraphrasing。
使用 `<a class="doc-link">` 添加突出的独立链接。

{% codeblock 示例 lang:html %}
这是第一段文字。

<p class="sidenote">第二段的注解。这段注解长一些。这段注解长一些。这段注解长一些。这段注解长一些。</p>

这是第二段文字。在屏幕宽度小于1200像素时，边注的样式会发生变化。缩小窗口来尝试这一特性。边注还有另一种样式，即TL;DR。

<p class="sidenote tldr">Note for paragraph 3.</p>

This is the third paragraph.

<a class="doc-link" href="../index.html">回到Wiki</a>
{% endcodeblock %}

<hr>

这是第一段文字。

<p class="sidenote">第二段的注解。这段注解长一些。这段注解长一些。</p>

这是第二段文字。在屏幕宽度小于1200像素时，边注的样式会发生变化。缩小窗口来尝试这一特性。边注还有另一种样式，即TL;DR。

<p class="sidenote tldr">Note for paragraph 3.</p>

This is the third paragraph.

<a class="doc-link" href="../index.html">回到Wiki</a>