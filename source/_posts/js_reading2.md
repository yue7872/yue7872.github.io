---
title: js读书笔记系列（二）
tags:
  - js
  - 红宝书
  - 读书笔记
categories: js基础
abbrlink: js
date: 2021-03-19 00:00:00
---



面试觉得自己实在太*垃圾*了，就来看看基础，做人还是要 **多读书**。
*****
# 在html中使用JavaScript

###  Script元素
#### 1. 转义
不要在代码任何地方出现"<\/script>"字符串，如
``` bash  
<script type="text/javascript"> 
	function sayScript(){ 
	alert("</script>"); 
 } 
</script>  
```
因为按照解析嵌入式代码的规则，当浏览器遇到字符串"<\/script>"时，就会认为那是结束的"<\/script>"标签。通过转义字符"\\"可以解决这个问题。（markdown也一样）。
像这样：
``` bash  
<script type="text/javascript"> 
	function sayScript(){ 
	alert("<\/script>"); 
 } 
</script>  
```
这样写代码浏览器可以接受，就不会出错了。
#### 2. 异步操作
解析嵌入式JavaScript代码和外部JavaScript文件（包括下载该文件）时，页面的处理也会暂时停止。
(1) 没有defer或async属性，浏览器会立即下载并执行相应的脚本，并且在下载和执行时页面的处理会停止。
(2) 有了defer属性，浏览器会立即下载相应的脚本，在下载的过程中页面的处理不会停止，等到文档解析完成后脚本才会执行。
(3) 有了async属性，浏览器会立即下载相应的脚本，在下载的过程中页面的处理不会停止，下载完成后立即执行，执行过程中页面处理会停止。
(4) 同时设置async和defer，则会遵从async而忽略defer属性。注：async、defer属性只适用于外部脚本文件。
(5) defer是"渲染完再执行"，async是"下载完就执行"。另外，如果有多个defer脚本，会按照它们在页面出现的顺序加载；而多个async脚本是不能保证加载顺序的,而是谁先下载完就执行谁，执行过程中页面处理会停止，但是其他脚本的下载不会停止。
![异步执行](/img/post/async.png)
其中蓝色代表js脚本网络下载时间，红色代表js脚本执行，绿色代表html解析。

**将脚本放在<\/body>前面就可以了，如果有依赖的则按照顺序放好。如果一定要放在head标签里面，最好是加defer属性。**

#### 3. 文档模式
文档类型（doctype）的切换可以实现不同的文档模式：混杂模式和标准模式。在文档开始处没有发现文档类型声明，则所有浏览器都会默认开启混杂模式。
​