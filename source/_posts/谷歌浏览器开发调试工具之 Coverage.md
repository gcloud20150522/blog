---
title: 谷歌浏览器开发调试工具之 Coverage
date: 2018-6-10 1:54:51
tags: 
  - chrome
  - 调试
  - 性能优化
categories: 性能优化
---
>Coverage 是chrome开发者工具的一个新功能，从字面意思上可以知道它是可以用来检测代码在网站运行时有哪些js和css是已经在运行，而哪些js和css是还没有用到的，如图，这是打开网页时，所显示的已运行和尚未运行的代码情况。

![pic1](/images/1.png)

如何打开caverage 

前提：chrome浏览器的版本必须是59或以上;

在ctrl+shift+i快速打开devtools，点击右上角的... More tools 有个Coverage。

功能

如上图所示，最右边显示的是我们加载的css和js文件数量，红色区域表示已运行的代码，而青色表示已加载但未运行的代码。可用来发现页面中尚未用到的js 和 css代码，你可以为用户只提供必要的代码，这样就可以提升页面的性能。这对于找出可以进行拆分的脚本以及延迟加载非关键脚本来说非常有用。
