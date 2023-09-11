---
caption: Flip Alignment Of Last Mate
title: Macro to flip alignment of the last inserted mate in SOLIDWORKS assembly
description: VBA macro which flips alignment (anti-aligned to aligned and vice-versa) for the last mate in the SOLIDWORKS assembly feature manager tree
---
这个VBA宏会找到活动的SOLIDWORKS装配体特征管理器树中的最后一个连接件。

对于这个连接件，对齐方式会从反对齐变为对齐，反之亦然。

{% code-snippet { file-name: Macro.vba } %}