---
caption: 合并相同组件
title: SOLIDWORKS BOM表中的合并相同组件命令
description: 模拟SOLIDWORKS BOM表中的合并相同组件命令的宏
image: combine-identical-components.png
---
![合并相同组件命令](combine-identical-components.png)

这个VBA宏演示了如何模拟SOLIDWORKS API中缺失的*合并相同组件*命令。

选择要合并相同组件的BOM表。默认情况下，所有组件都会被合并，但可以通过更改宏中**CombineIdenticalComponents**函数的参数来指定要合并的行。

{% code-snippet { file-name: Macro.vba } %}