---
layout: article
caption: 插入位置标签
title: 在绘图视图中添加位置标签
description: VBA宏演示如何在绘图视图中添加位置标签
image: location-label.png
---
![插入位置标签](location-label.png)

这个VBA宏提供了一个解决方案，用于在绘图视图中插入位置标签，因为SOLIDWORKS API中缺少此功能。

请将视图的名称指定为**VIEW_NAME**常量。

> 仅支持与位置标签兼容的视图，例如辅助视图、详图视图等。

{% code-snippet { file-name: Macro.vba } %}