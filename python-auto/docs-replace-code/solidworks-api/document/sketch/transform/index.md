---
title: Understanding transforms in sketches while using SOLIDWORKS API
caption: Understanding Sketch Transforms
description: Explanation of model to sketch and sketch to model transformations in SOLIDWORKS API to properly calculate the coordinates of sketch segments
image: sketch-coordinate-systems.png
labels: [transform,sketch]
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

~~~ vb
Dim swApp As SldWorks.SldWorks

Sub main()

    Set swApp = Application.SldWorks
    
    Dim swModel As SldWorks.ModelDoc2
    
    Set swModel = swApp.ActiveDoc
    
    Dim swSkPt As SldWorks.SketchPoint
    Set swSkPt = swModel.SelectionManager.GetSelectedObject6(1, -1)
    
    Debug.Print swSkPt.X & "; " & swSkPt.Y & "; " & swSkPt.Z
    
End Sub

~~~



## 从草图点检索全局坐标

为了找到相对于全局坐标系的坐标值，需要通过[SOLIDWORKS API属性ISketch::ModelToSketchTransform](https://help.solidworks.com/2018/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.ISketch~ModelToSketchTransform.html)找到草图到模型的变换矩阵，并将其应用于点的坐标。

下面的宏可以用于执行上一段中的步骤，但现在提取的坐标将与全局坐标系中的值匹配。

~~~ vb
Dim swApp As SldWorks.SldWorks

Sub main()

    Set swApp = Application.SldWorks
    
    Dim swModel As SldWorks.ModelDoc2
    
    Set swModel = swApp.ActiveDoc
    
    Dim swSkPt As SldWorks.SketchPoint
    Set swSkPt = swModel.SelectionManager.GetSelectedObject6(1, -1)
    
    Dim swSketch As SldWorks.Sketch
    Set swSketch = swSkPt.GetSketch
    
    'get the sketch to model transform (by inversing the model to sketch transform)
    Dim swTransform As SldWorks.MathTransform
    Set swTransform = swSketch.ModelToSketchTransform.Inverse
        
    Dim swMathUtils As SldWorks.MathUtility
    Set swMathUtils = swApp.GetMathUtility
    
    Dim dPt(2) As Double
    dPt(0) = swSkPt.X
    dPt(1) = swSkPt.Y
    dPt(2) = swSkPt.Z
    
    'create math point from the coordinate
    Dim swMathPt As SldWorks.MathPoint
    Set swMathPt = swMathUtils.CreatePoint(dPt)
    
    'multiple transform to move the point
    Set swMathPt = swMathPt.MultiplyTransform(swTransform)
    
    'read new coordinate values
    Dim vPt As Variant
    vPt = swMathPt.ArrayData
    
    Debug.Print vPt(0) & "; " & vPt(1) & "; " & vPt(2)
    
End Sub
~~~



## 根据全局坐标在草图中创建点

当需要根据全局坐标值在2D草图中创建草图点时，应使用逆变换。以下示例根据XYZ值在活动草图中插入一个草图点。

~~~ vb
Dim swApp As SldWorks.SldWorks

Sub main()

    Set swApp = Application.SldWorks
    
    Dim swModel As SldWorks.ModelDoc2
    
    Set swModel = swApp.ActiveDoc
        
    Dim swSketch As SldWorks.Sketch
    Set swSketch = swModel.SketchManager.ActiveSketch
    
    'get the model to sketch transform
    Dim swTransform As SldWorks.MathTransform
    Set swTransform = swSketch.ModelToSketchTransform
        
    Dim swMathUtils As SldWorks.MathUtility
    Set swMathUtils = swApp.GetMathUtility
    
    Dim dPt(2) As Double
    dPt(0) = 0.025
    dPt(1) = 0
    dPt(2) = 0.1
    
    'create math point from the coordinate
    Dim swMathPt As SldWorks.MathPoint
    Set swMathPt = swMathUtils.CreatePoint(dPt)
    
    'multiple transform to move the point
    Set swMathPt = swMathPt.MultiplyTransform(swTransform)
    
    'read new coordinate values
    Dim vPt As Variant
    vPt = swMathPt.ArrayData
    
    swModel.SketchManager.CreatePoint vPt(0), vPt(1), vPt(2)
    
End Sub
~~~

