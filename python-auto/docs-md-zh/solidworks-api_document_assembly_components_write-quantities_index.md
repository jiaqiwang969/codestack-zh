---
layout: sw-tool
title: 将SOLIDWORKS装配中的组件数量写入自定义属性
caption: 将组件数量写入自定义属性
description: 这是一个VBA宏，用于计算SOLIDWORKS装配中每个组件的总数量，并将其写入自定义属性。
image: bom-quantity.svg
labels: [数量, 组件]
group: 装配
---
这个VBA宏计算SOLIDWORKS装配中每个组件的总数量，并将其写入自定义属性。

这个宏可以与[从零件或装配组件导出平展图案](/solidworks-api/document/sheet-metal/export-all-flat-patterns/)和[导出到多种格式](/solidworks-api/import-export/export-multi-formats/)宏一起使用。

## 配置

可以通过更改宏开头的常量参数来配置宏，如下所示：

~~~ vb
Const PRP_NAME As String = "Qty" '要写入数量的自定义属性的名称
Const MERGE_CONFIGURATIONS As Boolean = False '将所有配置视为单个项目时为True
Const INCLUDE_BOM_EXCLUDED As Boolean = False '根据特征管理器树而不是BOM写入数量时为True
~~~

## 注意事项

* 宏将考虑通过自定义属性设置的用户分配的数量（UNIT_OF_MEASURE）
* 宏将考虑子组件的配置BOM选项（显示、推广或隐藏）
* 如果**MERGE_CONFIGURATIONS**设置为false，则宏将将数量属性写入配置；否则，将写入文档属性
* 如果组件不在当前范围内（例如，从BOM中排除了组件），宏将不会清除现有的数量
* 对于未加载的组件（例如轻量级组件），宏将失败
* 宏将尝试解析所有轻量级组件

{% code-snippet { file-name: Macro.vba } %}