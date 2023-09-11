---
title: 使用SOLIDWORKS API创建精确零件边界框
caption: 创建精确边界框
description: 使用SOLIDWORKS API在零件文档中创建精确边界框的宏
image: precise-bounding-box.png
labels: [边界框, 极值点]
---
![零件文档中的精确边界框](precise-bounding-box.png){ width=250 }

根据SOLIDWORKS API帮助文档中[IPartDoc::GetPartBox](https://help.solidworks.com/2016/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.ipartdoc~getpartbox.html)方法（或其他边界框API）的*备注*部分所述：

> 返回的值是近似值，不应用于比较或计算目的。此外，在重建模型后，边界框可能会发生变化。

要计算精确边界框，需要通过[IBody2::GetExtremePoint](https://help.solidworks.com/2016/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.ibody2~getextremepoint.html)在XYZ方向上找到每个实体的极值点。

以下宏将使用SOLIDWORKS API的两种方法计算活动零件文档的边界框、宽度、高度和长度。

结果将创建带有边界框的3D草图。

### 精度

近似计算的边界框可能会有超过10%的误差。对于以下[示例零件](bbox-precision.SLDPRT)，边界框体积之间的差异为14%。以下图像显示了差异（绿色框是精确计算，红色框是近似计算）：

![前视图](bbox-front-view.png){ width=250 }

![顶视图](bbox-top-view.png){ width=250 }

![右视图](bbox-right-view.png){ width=250 }

> 通过极值点计算的精确边界框与SOLIDWORKS 2018中添加的[边界框特征](https://help.solidworks.com/2018/English/WhatsNew/t_bounding_box_for_part_assem.htm)创建的边界框完全相等。

### 性能

提取近似框的速度比精确框快300多倍。对于单个实体零件，近似计算边界框花费了0.016毫秒，而精确计算相同零件花费了5.57毫秒。对于包含63个实体的多实体零件，近似计算花费了0.018毫秒，而精确计算花费了16.68毫秒。

总结起来，平均而言，每秒可以计算超过60000个近似边界框，而只能计算约50个精确边界框（超过1000倍的差异）。

### 通过极值点计算精确边界框

{% code-snippet { file-name: GetPreciseBoundingBox.vba } %}

### 计算近似边界框

{% code-snippet { file-name: GetBoundingBox.vba } %}