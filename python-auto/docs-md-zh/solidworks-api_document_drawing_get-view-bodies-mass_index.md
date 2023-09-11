---
title: 使用SOLIDWORKS API获取绘图视图中物体的质量
caption: 从绘图视图中获取质量
description: 使用SOLIDWORKS API，在所选绘图视图中找到所有物体的总质量的C# VSTA宏示例
image: multi-body-sheet-metal-mass-property.png
labels: [视图,质量,展开图案]
---
可以使用[SOLIDWORKS API的IBody2::GetMassProperties](https://help.solidworks.com/2016/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.ibody2~getmassproperties.html)方法来找到特定物体的质量，但需要指定密度才能计算质量，这可能不容易提取。

如果需要找到绘图视图中物体的质量，这种方法可能不适用。如果将材料应用于物体本身，则该物体的密度不可用。可以从材料属性中提取密度，但需要[解析材料XML文件](http://localhost:4000/solidworks-api/document/materials/copy-custom-property/)以找到节点的值。

![展开图案的绘图视图](flat-pattern-drawing.png){ width=250 }

另一种选择是使用[IMassProperty](https://help.solidworks.com/2017/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.IMassProperty.html)接口。

![零件文档中的物体质量](multi-body-sheet-metal-mass-property.png){ width=450 }

然而，在绘图上下文中提取的物体指针不适用于计算。在这种情况下，质量值始终为0。需要将物体指针转换为相应配置中的零件上下文。

以下是使用SOLIDWORKS API获取所选绘图视图中所有物体质量的C# VSTA宏代码，并在消息框中显示结果。

{% code-snippet { file-name: SolidWorksMacro.cs } %}