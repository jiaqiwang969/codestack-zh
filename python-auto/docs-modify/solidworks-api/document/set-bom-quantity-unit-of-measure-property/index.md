---
title: Set BOM Quantity (Unit Of Measure) property using SOLIDWORKS API
caption: Set BOM Quantity (Unit Of Measure) Property In The Model
description: Example demonstrates how to modify the BOM quantity field in the properties dialog
image: bom-quantity-property.png
labels: [bom quantity, example, qty, unit of measure]
redirect-from:
  - /2018/03/set-bom-quantity-unit-of-measure.html
---
本示例演示了如何使用SOLIDWORKS API修改属性对话框中的BOM数量字段。

![指定与计量单位相关联的属性的选项](bom-quantity-property.png){ width=640 height=170 }

此选项允许覆盖BOM表中组件的数量值。

![显示修改后的组件数量的BOM表](bom-table-unit-of-measure.png){ width=640 }

要更改此属性，需要通过[SOLIDWORKS API接口ICustomPropertyManager](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.icustompropertymanager.html)设置隐藏的*UNIT_OF_MEASURE*自定义属性。

{% code-snippet { file-name: Macro.vba } %}