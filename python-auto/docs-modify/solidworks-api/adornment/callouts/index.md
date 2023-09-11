---
title: Using Callouts object for model annotation in SOLIDWORKS API
caption: Callouts
description: Using Callouts for annotating models (similar to balloons), linking to the entities and displaying custom data using SOLIDWORKS API
order: 1
labels: [callout, balloons]
---
在SOLIDWORKS中，Callouts是类似气球的对象，可以附加到实体上（通常通过选择），并显示有关实体的附加信息。Callouts不会随着模型的缩放而改变大小，并且即使模型旋转，它们也会保持相同的方向。

Callouts是临时对象，通常在选择清除或操作完成后被销毁。

SOLIDWORKS中最常见的Callouts示例是测量工具。当选择实体时，测量结果会显示在Callouts中。

SOLIDWORKS API通过[ISwCalloutHandler接口](https://help.solidworks.com/2018/english/api/swpublishedapi/solidworks.interop.swpublished~solidworks.interop.swpublished.iswcallouthandler.html)提供了创建Callouts的能力。该处理程序允许创建Callouts的定义并处理相关事件。

Callouts可以以只读方式显示，也可以捕获用户输入的值。Callouts可以具有不同的颜色，可以是单行或多行。

本节包含使用SOLIDWORKS API创建、显示和处理Callouts事件的宏和代码示例。