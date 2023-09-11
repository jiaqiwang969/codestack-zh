---
layout: sw-tool
title: 导出选定实体到外部格式的宏
caption: 导出选定实体
description: VBA宏，仅导出选定的实体到外部格式（例如3D xml、xaml、amf、3mf）
image: export-bodies.svg
labels: [导出, 实体]
group: 导入/导出
---
当将零件文件导出到SOLIDWORKS支持的大多数外部格式时，可以选择导出的实体范围，从而只处理选定的实体。

![导出实体对话框](export-dialog.png)

然而，并非所有格式都支持此功能。例如，3D xml、xaml、amf、3mf等格式将始终导出所有实体，而不考虑选择。

此VBA宏允许仅将选定的实体导出到SOLIDWORKS支持的任何格式。

选择实体、面、边或顶点，运行宏并指定导出的名称以生成结果。

{% code-snippet { file-name: Macro.vba } %}