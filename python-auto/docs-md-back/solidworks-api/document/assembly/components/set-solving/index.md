---
layout: sw-tool
title: Set multiple assembly components solving (rigid or flexible) using SOLIDWORKS API
caption: Set Components Solving (Rigid or Flexible)
description: VBA macro to batch set the rigid or flexible option for selected components in the assembly using SOLIDWORKS API
image: batch-set-solving.png
labels: [batch,solving,rigid,flexible]
group: Assembly
---
![设置多个装配组件的求解](batch-set-solving.png)

用户可以使用组件选项页面或工具栏命令更改装配组件的求解选项（刚性或柔性）。然而，这仅限于一次只能更改一个组件。

![组件页面的求解选项](solving-options.png)

这个VBA宏允许使用SOLIDWORKS API一次性为所有选定的组件设置刚性或柔性选项。

请按以下方式指定选项：

~~~ vb
Const SET_FLEXIBLE As Boolean = True 'True - 设置为柔性，False - 设置为刚性
~~~

{% code-snippet { file-name: Macro.vba } %}