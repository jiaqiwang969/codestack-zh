---
title: 使用SOLIDWORKS API在绘图视图中选择实体
caption: 在绘图视图中选择实体
description: 本示例演示了使用SOLIDWORKS API在绘图视图中选择实体（例如边缘、面、顶点）的不同方法。
image: circular-edge-selected-in-views.png
---
![在3个绘图视图中选择了命名边缘](circular-edge-selected-in-views.png){ width=300 }

本示例演示了使用SOLIDWORKS API在绘图视图中选择实体（例如边缘、面、顶点）的不同方法。

1. 通过直接使用[IView:SelectEntity](https://help.solidworks.com/2012/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IView~SelectEntity.html)方法在目标视图中选择实体。当需要选择实体而无需传递任何附加数据（例如选择标记或标注）时，此方法非常有用。
2. 通过在选择数据中指定视图，使用[ISelectData::View](https://help.solidworks.com/2012/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.ISelectData~View.html) SOLIDWORKS API属性选择实体。与前一种方法相比，这种方法更加灵活，因为可以提供更多的选择信息。
3. 选择可视实体。这种方法允许在绘图视图的上下文中查找实体。其主要优点是它只会尝试选择当前视图方向中可见的实体，而前两种方法不考虑实体被其他实体遮挡的情况。

* 要运行宏，请下载[示例模型和绘图](plate-with-hole.zip)。
* 在零件文档中，圆形边缘被命名为“孔”。

![在SOLIDWORKS零件中命名的边缘](named-edge.png){ width=300 }

* 运行宏后，此边缘将在3个视图中使用上述3种不同的方法被选择。

{% code-snippet { file-name: Macro.vba } %}