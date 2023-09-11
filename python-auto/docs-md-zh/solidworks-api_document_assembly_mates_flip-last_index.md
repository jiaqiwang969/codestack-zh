---
caption: 翻转最后一个连接件的对齐方式
title: SOLIDWORKS装配体中翻转最后一个插入连接件的宏
description: 这是一个VBA宏，用于在SOLIDWORKS装配体的特征管理器树中翻转最后一个连接件的对齐方式（从反对齐到对齐，反之亦然）。
---
这个VBA宏会找到活动的SOLIDWORKS装配体特征管理器树中的最后一个连接件。

对于这个连接件，对齐方式会从反对齐变为对齐，反之亦然。

{% code-snippet { file-name: Macro.vba } %}