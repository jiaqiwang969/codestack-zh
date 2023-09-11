---
title: 使用SOLIDWORKS API理解草图中的变换
caption: 理解草图变换
description: 解释SOLIDWORKS API中模型到草图和草图到模型变换，以正确计算草图线段的坐标
image: sketch-coordinate-systems.png
labels: [变换,草图]
---
在处理草图线段（如线、弧等）或点时，需要考虑到从SOLIDWORKS API返回的坐标值（例如[ISketchPoint::X](https://help.solidworks.com/2017/English/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.ISketchPoint~X.html)属性）是相对于局部草图坐标系的。

这些值在3D草图或在Front平面上创建的2D草图（如果未移动）中是相同的，但在其他情况下会有所不同。

如下图所示，点的值在局部草图坐标系中显示为{-50, 10, 0}（在草图点属性管理器页面），而在全局坐标系中显示为{-50, 0, -10}（在SOLIDWORKS状态栏中）。这种差异是因为2D草图是在Top平面上创建的。

![局部和全局坐标系的不同值。](global-local-coordinates.png){ width=450 }

激活草图时，2D草图的局部坐标系用红色的X和Y箭头表示。全局坐标系用红色、绿色和蓝色的三轴表示在SOLIDWORKS模型窗口的右下角。

![局部草图坐标系和全局坐标系](sketch-coordinate-systems.png){ width=350 }

## 从草图点读取局部坐标

以下宏读取所选草图点相对于局部草图坐标系的坐标，并将其输出到SOLIDWORKS的即时窗口中。

![提取的草图点坐标](coordinate-output.png){ width=350 }

* 在Front平面上创建一个草图并创建一个草图点
* 选择此点
* 运行宏并与全局坐标值进行比较（结果以米为单位打印）
* 值将匹配

![草图点的全局坐标](sketch-point-coordinate.png){ width=350 }

* 在任何平面上创建新的草图，但不是Front平面（例如Top平面）
* 重复上述步骤
* 现在坐标不匹配。

{% code-snippet { file-name: NoTransformsMacro.vba } %}

## 从草图点检索全局坐标

为了找到相对于全局坐标系的坐标值，需要通过[SOLIDWORKS API属性ISketch::ModelToSketchTransform](https://help.solidworks.com/2018/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.ISketch~ModelToSketchTransform.html)找到草图到模型的变换矩阵，并将其应用于点的坐标。

下面的宏可以用于执行上一段中的步骤，但现在提取的坐标将与全局坐标系中的值匹配。

{% code-snippet { file-name: TransformSketchCoordinateMacro.vba } %}

## 根据全局坐标在草图中创建点

当需要根据全局坐标值在2D草图中创建草图点时，应使用逆变换。以下示例根据XYZ值在活动草图中插入一个草图点。

{% code-snippet { file-name: CreateSketchPointFromGlobalCoordinate.vba } %}