---
title: VBA宏隐藏SOLIDWORKS文件树中的所有选定特征
caption: 在树中隐藏特征
description: VBA宏可隐藏特征并使其在SOLIDWORKS特征管理器树中不可见
image: hidden-features.png
labels: [特征,隐藏,不可见]
---
这个VBA宏允许在树中使选定的特征不可见。这些特征仍然可以在图形区域中完全运作和可见（例如平面），但在特征管理器树中不可见。

甚至默认特征（如平面）也可以被隐藏。

![在特征管理器树中隐藏的草图、右侧和顶部平面](hidden-features.png)

要显示隐藏的特征，请使用[显示隐藏特征](/solidworks-api/document/features-manager/reveal-hidden-features/)宏。

{% code-snippet { file-name: Macro.vba } %}