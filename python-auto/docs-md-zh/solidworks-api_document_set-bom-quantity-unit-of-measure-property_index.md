---
title: 使用SOLIDWORKS API设置BOM数量（计量单位）属性
caption: 在模型中设置BOM数量（计量单位）属性
description: 本示例演示了如何使用SOLIDWORKS API修改属性对话框中的BOM数量字段。
image: bom-quantity-property.png
labels: [BOM数量, 示例, 数量, 计量单位]
redirect-from:
  - /2018/03/set-bom-quantity-unit-of-measure.html
---
本示例演示了如何使用SOLIDWORKS API修改属性对话框中的BOM数量字段。

![指定与计量单位相关联的属性的选项](bom-quantity-property.png){ width=640 height=170 }

此选项允许覆盖BOM表中组件的数量值。

![显示修改后的组件数量的BOM表](bom-table-unit-of-measure.png){ width=640 }

要更改此属性，需要通过[SOLIDWORKS API接口ICustomPropertyManager](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.icustompropertymanager.html)设置隐藏的*UNIT_OF_MEASURE*自定义属性。

{% code-snippet { file-name: Macro.vba } %}