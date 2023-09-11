---
title: SOLIDWORKS commands manager with SwEx.AddIn framework
caption: Commands Manager
description: Instructions on adding commands (menu, toolbar and context menu) with SwEx.AddIn framework for developing SOLIDWORKS add-ins in C# and VB.NET
toc-group-name: labs-solidworks-swex
order: 2
---
通过将枚举类型视为命令组，将枚举值视为命令项，SwEx简化了添加命令的过程。可以使用各种属性对值进行修饰，以提供自定义的标题、描述和图标。

命令可以插入到菜单、工具栏或上下文菜单中。

用户可以处理命令的点击事件，并为命令按钮分配自定义状态。

在同一个插件中可以插入多个命令组。