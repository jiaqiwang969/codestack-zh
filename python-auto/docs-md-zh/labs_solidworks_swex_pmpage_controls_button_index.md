---
title: SOLIDWORKS属性管理器页面中的按钮控件
caption: 按钮
description: 使用SwEx.PMPage框架在属性管理器页面中创建按钮控件
image: button.png
toc-group-name: labs-solidworks-swex
order: 10
---
![按钮控件](button.png)

要在属性管理器页面中创建一个按钮，需要声明一个委托类型为[Action](https://docs.microsoft.com/zh-cn/dotnet/api/system.action?view=netframework-4.8)的属性。

指向void函数的指针分配给该属性，作为按钮的处理程序：

{% code-snippet { file-name: Button.* } %}