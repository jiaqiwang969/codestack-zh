---
title: Button control in SOLIDWORKS property Manager Page
caption: Button
description: Creating button control in the Property Manager Page using SwEx.PMPage framework
image: button.png
toc-group-name: labs-solidworks-swex
order: 10
---
![按钮控件](button.png)

要在属性管理器页面中创建一个按钮，需要声明一个委托类型为[Action](https://docs.microsoft.com/zh-cn/dotnet/api/system.action?view=netframework-4.8)的属性。

指向void函数的指针被分配给该属性，作为按钮的处理程序：

{% code-snippet { file-name: Button.* } %}