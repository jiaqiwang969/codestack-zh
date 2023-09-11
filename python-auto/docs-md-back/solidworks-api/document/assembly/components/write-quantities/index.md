---
layout: sw-tool
title: Write component quantity in the SOLIDWORKS assembly to custom property
caption: Write Component Quantity To Custom Property
description: VBA macro which writes the total quantities of components in SOLIDWORKS assembly into custom property
image: bom-quantity.svg
labels: [quantity,component]
group: Assembly
---
这个VBA宏可以计算SOLIDWORKS装配中每个组件的总数量，并将其写入自定义属性。

这个宏可以与[从零件或装配组件导出平展图案](/solidworks-api/document/sheet-metal/export-all-flat-patterns/)和[导出到多种格式](/solidworks-api/import-export/export-multi-formats/)宏一起使用。

## 配置

可以通过更改宏开头的常量参数来配置宏，如下所示：

~~~ vb
Const PRP_NAME As String = "Qty" '要写入数量的自定义属性的名称
Const MERGE_CONFIGURATIONS As Boolean = False '将所有配置视为单个项目时为True
Const INCLUDE_BOM_EXCLUDED As Boolean = False '根据特征管理器树而不是BOM写入数量时为True
~~~

## 注意事项

* 宏将考虑通过自定义属性（UNIT_OF_MEASURE）设置的用户分配的数量
* 宏将考虑子组件的配置BOM选项（显示、推广或隐藏）
* 如果**MERGE_CONFIGURATIONS**设置为false，则宏将将数量属性写入配置；否则，将写入文档属性
* 如果组件不在当前范围内（例如，如果组件在BOM中被排除），宏将不会清除现有的数量
* 宏将无法处理未加载的组件（例如，轻量级组件）
* 宏将尝试解析所有轻量级组件

{% code-snippet { file-name: Macro.vba } %}