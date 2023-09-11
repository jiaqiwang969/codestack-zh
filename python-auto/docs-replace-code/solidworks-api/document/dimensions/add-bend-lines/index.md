---
title: Add dimensions to bend lines using SOLIDWORKS API
caption: Add Dimensions To Bend Lines
description: Example demonstrates how to add dimensions to bend lines in the drawing view of sheet metal flat pattern
image: sw-bend-lines.png
labels: [bend lines, dimension, example, solidworks api]
redirect-from:
  - /2018/03/solidworks-api-dimensions-dimension-bend-lines.html
---
本示例演示了如何使用SOLIDWORKS API在钣金展开图的绘图视图中为弯曲线添加尺寸。

![在钣金展开图绘图中的弯曲线之间添加尺寸](sw-bend-lines.png){ width=400 height=150 }

需要使用带有分配视图的选择数据对象来选择草图线，否则创建尺寸将失败。

使用[IModelDoc2::AddDimension2](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.imodeldoc~adddimension2.html) SOLIDWORKS API来添加尺寸。尺寸定位在坐标(0, 0, 0)处。请参考[尺寸可见实体](/solidworks-api/document/drawing/view-dimension-drawing-entities/)示例中的代码片段来计算最佳尺寸位置。

~~~ vb
Dim swApp As SldWorks.SldWorks
Dim swModel As SldWorks.ModelDoc2
Dim swSelMgr As SldWorks.SelectionMgr
Dim swView As SldWorks.View

Sub main()

    Set swApp = Application.SldWorks

    Set swModel = swApp.ActiveDoc
    
    If Not swModel Is Nothing Then
    
        Set swSelMgr = swModel.SelectionManager
        
        Set swView = swSelMgr.GetSelectedObject6(1, -1)
        
        If Not swView Is Nothing Then
        
            Dim vBendLines As Variant
            vBendLines = swView.GetBendLines
            
            If UBound(vBendLines) >= 1 Then
            
                Dim swSelData As SldWorks.SelectData
                Set swSelData = swSelMgr.CreateSelectData
                swSelData.View = swView 'must be set
                
                swModel.ClearSelection2 True
                
                Dim i As Integer
                
                For i = 0 To 1
                    
                    Dim swSkSeg As SldWorks.SketchSegment
                                        
                    Set swSkSeg = vBendLines(i)
                    
                    swSkSeg.Select4 True, swSelData
                    
                Next
                
                swModel.AddDimension2 0, 0, 0
                
            Else
                MsgBox "There should be at least 2 bend lines in the drawing view"
            End If
            
        Else
            MsgBox "Please select drawing view with flat pattern"
        End If
    
    Else
        MsgBox "Please open drawing"
    End If
End Sub


~~~

