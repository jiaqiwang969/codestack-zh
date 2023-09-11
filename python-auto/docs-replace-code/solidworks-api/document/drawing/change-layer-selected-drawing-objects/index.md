---
layout: sw-tool
title: SOLIDWORKS macro to change layer of selected objects in drawing using SOLIDWORKS API
caption: Change Layer For Selected Objects In Drawing
description: Macro will move all selected objects in the drawing sheet to specified layer using SOLIDWORKS API
image: sw-drawing-layers.png
labels: [drawing, layer, solidworks api, utility]
group: Drawing
redirect-from:
  - /2018/03/solidworks-api-drawing-change-layer-for-selected-objects.html
---

该宏将使用SOLIDWORKS API将绘图工作表中的所有选定对象移动到指定的图层。

![绘图图层](sw-drawing-layers.png){ width=400 }

SOLIDWORKS API没有通用的::Layer属性来更改任何实体的图层，而是将此属性添加到支持它的每个接口中（例如[ISketchSegment::Layer](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isketchsegment~layer.html)属性）。该宏检查实体的类型，并调用相应的SOLIDWORKS API属性来更改图层。

~~~ vb
Dim swApp As SldWorks.SldWorks
Dim swDraw As SldWorks.DrawingDoc
Dim swSelMgr As SldWorks.SelectionMgr

Sub main()
    
    On Error Resume Next
    
    Set swApp = Application.SldWorks
    
    Set swDraw = swApp.ActiveDoc
    
    If Not swDraw Is Nothing Then
        
        Set swSelMgr = swDraw.SelectionManager
        
        If swSelMgr.GetSelectedObjectCount2(-1) > 0 Then
            
            Dim layerName As String
            layerName = InputBox("Specify the layer name to move selected objects to")
            
            Dim swAnn As SldWorks.Annotation
            
            Dim i As Integer
                        
            For i = 1 To swSelMgr.GetSelectedObjectCount2(-1)
                    
                Dim swSelObj As Object
                Set swSelObj = swSelMgr.GetSelectedObject6(i, -1)
                
                If TypeOf swSelObj Is SldWorks.SketchSegment Then
                    
                    Dim swSkSegment As SldWorks.SketchSegment
                    Set swSkSegment = swSelObj
                    swSkSegment.Layer = layerName
                
                ElseIf TypeOf swSelObj Is SldWorks.SketchPoint Then
                    
                    Dim swSkPoint As SldWorks.SketchPoint
                    Set swSkPoint = swSelObj
                    swSkPoint.Layer = layerName
                    
                ElseIf TypeOf swSelObj Is SldWorks.Note Then
                    
                    Dim swNote As SldWorks.Note
                    Set swNote = swSelObj
                    Set swAnn = swNote.GetAnnotation()
                    swAnn.Layer = layerName
                    
                ElseIf TypeOf swSelObj Is SldWorks.DisplayDimension Then
                    
                    Dim swDispDim As SldWorks.DisplayDimension
                    Set swDispDim = swSelObj
                    Set swAnn = swDispDim.GetAnnotation
                    swAnn.Layer = layerName
                    
                Else 'try to set the layer using late binding
                    swSelObj.Layer = layerName
                End If
                    
            Next
        Else
            MsgBox "Please select annotation, sketch segment or point to move to new layer"
        End If
        
    Else
        MsgBox "Please open drawing"
    End If
    
End Sub

~~~

