---
layout: sw-tool
title: 使用SOLIDWORKS API设置多个装配组件的求解（刚性或柔性）
caption: 设置组件求解（刚性或柔性）
description: 使用SOLIDWORKS API批量设置装配中所选组件的刚性或柔性选项的VBA宏
image: batch-set-solving.png
labels: [批量,求解,刚性,柔性]
group: 装配
---
![设置多个装配组件的求解](batch-set-solving.png)

用户可以使用组件选项页面或工具栏命令更改装配组件的求解选项（刚性或柔性）。然而，这仅限于一次只能更改一个组件。

![组件选项页面的求解选项](solving-options.png)

这个VBA宏允许使用SOLIDWORKS API一次命令为所有选定的组件设置刚性或柔性选项。

请按以下方式指定选项：

~~~ vb
Const SET_FLEXIBLE As Boolean = True 'True - 设置为柔性，False - 设置为刚性
~~~

{% code-snippet { file-name: Macro.vba } %}