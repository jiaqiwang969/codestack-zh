---
layout: sw-tool
title: Macro to select equal arcs in the sketch using SOLIDWORKS API
caption: Select Equal Arcs
description: VBA macro to find and select all arcs with diameter equal to the input arc using SOLIDWORKS API
image: selected-equal-arcs.png
labels: [sketch,arc,circle,equal]
group: Sketch
---
![在草图中选择相等弧](selected-equal-arcs.png){ width=350 }

这个VBA宏选择与预选输入草图弧相等大小的草图弧。只选择原始输入弧所在草图中的弧。该宏适用于活动和非活动草图。

## 选项

可以通过更改宏开头的常量的值来配置宏

~~~ vb
Const EPS As Double = 0.0000000001 '弧半径比较容差
~~~

~~~ vb
Const EPS As Double = 0.0000000001

Dim swApp As SldWorks.SldWorks

Sub main()

    Set swApp = Application.SldWorks
    
    On Error GoTo catch
    
try:
    Dim swModel As SldWorks.ModelDoc2
    
    Set swModel = swApp.ActiveDoc
    
    If Not swModel Is Nothing Then
        
        Dim swSkSrcArc As SldWorks.SketchArc
        Set swSkSrcArc = swModel.SelectionManager.GetSelectedObject6(1, -1)
        
        If Not swSkSrcArc Is Nothing Then
            
            Dim radius As Double
            radius = swSkSrcArc.GetRadius()
            
            Dim swSketch As SldWorks.Sketch
            Set swSketch = swSkSrcArc.GetSketch
            
            Dim vSegs As Variant
            vSegs = swSketch.GetSketchSegments()
            
            Dim i As Integer
            
            For i = 0 To UBound(vSegs)
                
                Dim swSkSeg As SldWorks.SketchSegment
                Set swSkSeg = vSegs(i)
                
                If swSkSeg.GetType() = swSketchSegments_e.swSketchARC Then
                
                    If Not swSkSrcArc Is swSkSeg Then
                    
                        Dim swSkArc As SldWorks.SketchArc
                        Set swSkArc = swSkSeg
                        
                        If Abs(swSkArc.GetRadius() - radius) < EPS Then
                            swSkSeg.Select4 True, Nothing
                        End If
                        
                    End If
                End If
                
            Next
            
        Else
            Err.Raise vbError, "", "Please select sketch arc"
        End If
        
    Else
        Err.Raise vbError, "", "Open model"
    End If
    
    GoTo finally
catch:
    swApp.SendMsgToUser2 Err.Description, swMessageBoxIcon_e.swMbStop, swMessageBoxBtn_e.swMbOk
finally:
    
End Sub

~~~

