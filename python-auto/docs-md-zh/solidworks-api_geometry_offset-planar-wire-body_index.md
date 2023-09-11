---
title: 使用SOLIDWORKS API对平面曲线（线体）进行偏移
caption: 偏移平面线体
description: 使用SOLIDWORKS API的VBA宏示例，对平面曲线（线体）进行偏移并显示偏移预览
image: offset-wire-body.png
labels: [线体, 偏移]
---
这个VBA示例演示了如何使用SOLIDWORKS API对SOLIDWORKS曲线的线体进行偏移，并显示预览。

线体是一种对应于边和曲线的实体。

线体在复合曲线、通过XYZ曲线等特征中使用。这些实体也用于生成某些类型的预览，例如倒角特征的预览。

![倒角预览](fillet-preview.png){ width=350 }

要运行这个示例：

* 在正面平面上创建一个复合曲线（或其他类型的曲线），即法线为{0, 0, 1}。
* 运行宏。宏从所选曲线中提取线体。该线体将是一个线体。宏将该线体偏移10毫米，并显示偏移的预览。
* 宏停止执行。一旦继续执行，临时实体将被销毁。

![偏移线体](offset-wire-body.png){ width=450 }

{% code-snippet { file-name: Macro.vba } %}