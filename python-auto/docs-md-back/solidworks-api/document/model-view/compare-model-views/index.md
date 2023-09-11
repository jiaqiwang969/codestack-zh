---
title: Compare model views transformations using SOLIDWORKS API
caption: Compare Model Views
description: Example demonstrates how to compare 2 model views (by orientation, translation and scale)
image: view-orientation.png
---
![模型视图方向](view-orientation.png){ width=250 }

这个示例演示了如何使用SOLIDWORKS API比较零件或装配中的两个模型视图。

宏将识别变化并显示结果，如果：

* 视图相同
* 视图方向不同（即旋转）
* 视图平移不同（即移动）
* 视图缩放不同

宏使用[用户定义类型](visual-basic/data-structures/types/) **ViewData** 来存储视图的方向、平移和缩放。这个结构与视图没有关联，表示视图变换的快照。

**CompareViewData** 函数的结果被定义为 *CompareViewResult_e* [标志枚举器](visual-basic/data-structures/enumerators#flag-enumerator-multiple-options)。这允许返回视图方向的特定变化或变化的组合。

* 打开模型并启动宏。
* 一旦读取了第一个视图的数据，宏将暂停执行。
* 更改视图并继续执行宏。
* 结果将显示在消息框中。

{% code-snippet { file-name: Macro.vba } %}