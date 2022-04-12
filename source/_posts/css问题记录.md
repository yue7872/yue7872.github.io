---
title: css问题记录
date: 4/06/2022 17:56:08
tags: [css,记录]
categories: css
abbrlink: css
---

# css问题记录

#### 1. after/before 的content设为中文字符，浏览器偶尔显示乱码

解决方案： 把中文字符转化为unicode编码。工具： https://tool.chinaz.com/Tools/Unicode.aspx

转化后生成的编码中，把u去掉，如删除 => \u5220\u9664\u000d\u000a => \5220\9664\000d\000a，用这个编码替换掉原来的content即可。

