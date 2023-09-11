---
title: 使用SwEx.AddIn框架的SOLIDWORKS命令管理器
caption: 命令管理器
description: 使用SwEx.AddIn框架在C#和VB.NET中开发SOLIDWORKS插件时，添加命令（菜单、工具栏和上下文菜单）的说明。
toc-group-name: 实验室-SOLIDWORKS-SwEx
order: 2
---
通过将枚举类型视为命令组，将枚举值视为命令项，SwEx简化了添加命令的过程。可以使用各种属性对值进行修饰，以提供自定义的标题、描述和图标。

命令可以插入到菜单、工具栏或上下文菜单中。

用户可以处理命令的点击事件，并为命令按钮分配自定义状态。

在同一个插件中可以插入多个命令组。