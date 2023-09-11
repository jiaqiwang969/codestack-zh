---
title: Offset planar curve (wire body) using SOLIDWORKS API
caption: Offset Planar Wire Body
description: VBA macro example to offset planar curve (wire body) and display the offset preview using SOLIDWORKS API
image: offset-wire-body.png
labels: [body,wire,offset]
---
这个VBA示例演示了如何使用SOLIDWORKS API对SOLIDWORKS曲线的线体进行偏移，并显示预览。

线体是一种对应于边和曲线的实体。

线体在复合曲线、通过XYZ曲线等特征中使用。这些实体也用于生成某些类型的预览，例如倒角特征的预览。

![倒角预览](fillet-preview.png){ width=350 }

要运行这个示例：

* 在正面平面上创建一个复合曲线（或其他类型的曲线），即法线为{0, 0, 1}。
* 运行宏。宏从所选曲线中提取线体。该线体将是一个线体。宏将该线体偏移10毫米，并显示偏移的预览。
* 宏停止执行。一旦继续执行，临时实体将被销毁。

![偏移线体](offset-wire-body.png){ width=450 }

~~~ vb
Dim swApp As SldWorks.SldWorks

Sub main()

    Set swApp = Application.SldWorks
    
    Dim swModel As SldWorks.ModelDoc2
    
    Set swModel = swApp.ActiveDoc
    
    If Not swModel Is Nothing Then
        
        Dim swSelMgr As SldWorks.SelectionMgr
        Set swSelMgr = swModel.SelectionManager
        
        Dim swEdge As SldWorks.Edge
        Set swEdge = swSelMgr.GetSelectedObject6(1, -1)
        
        If Not swEdge Is Nothing Then
        
            Dim swBody As SldWorks.Body2
            Set swBody = swEdge.GetBody()
            
            If swBody.GetType() = swBodyType_e.swWireBody Then
                
                Dim swOffsetBody As SldWorks.Body2
                Dim swNormVec As SldWorks.MathVector
                
                Dim swMathUtils As SldWorks.MathUtility
                Set swMathUtils = swApp.GetMathUtility
                
                Dim dVec(2) As Double
                dVec(0) = 0: dVec(1) = 0: dVec(2) = 1
                
                Set swNormVec = swMathUtils.CreateVector(dVec)
                
                Set swOffsetBody = swBody.OffsetPlanarWireBody(0.01, swNormVec, swOffsetPlanarWireBodyOptions_e.swOffsetPlanarWireBodyOptions_GapFillExtend)
                
                If swOffsetBody Is Nothing Then
                    Err.Raise vbError, "", "Failed to create offset body. Make sure that selected edge is on a plane with the normal specified in dVec variable"
                End If
                
                swOffsetBody.Display3 swModel, RGB(255, 255, 0), swTempBodySelectOptions_e.swTempBodySelectOptionNone
                
                Stop
                
                Set swOffsetBody = Nothing
                
            Else
                Err.Raise vbError, "", "Selected edge is not a wire body"
            End If
        
        Else
            Err.Raise "Edge is not selected"
        End If
        
    Else
        Err.Raise "Document is not open"
    End If
    
End Sub
~~~

