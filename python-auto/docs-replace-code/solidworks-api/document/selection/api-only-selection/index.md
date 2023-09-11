---
title: Selecting SOLIDWORKS Objects for API only
caption: Selecting Objects For API Only
description: Example shows how to select the object for API purpose only (without graphics selection) preserving current user selections
image: extrude-direction-up-to-surface.png
labels: [selection, extrude]
---
![沿着线方向将挤压的草图弧形延伸到平面表面](extrude-direction-up-to-surface.png){ width=500 }

这个示例展示了如何通过仅选择用于API目的的输入（不包括图形选择），保留当前用户的选择，在SOLIDWORKS零件中创建挤压特征。

运行宏的步骤：

* 下载示例文件并在SOLIDWORKS中打开[挤压选择示例](extrude-selection-example.SLDPRT)
* 选择任意对象（例如前平面和右平面）
* 逐步调试宏。宏会在数据库中直接预先选择所需的对象用于挤压特征（对用户不可见）

结果是创建了指定方向的挤压特征，延伸到指定的表面，并且保留了所有原始用户的选择。

~~~ vb
Dim swApp As SldWorks.SldWorks
Dim swModel As SldWorks.ModelDoc2
Dim swSelMgr As SldWorks.SelectionMgr

Sub main()

    Set swApp = Application.SldWorks

    Set swModel = swApp.ActiveDoc
    
    If Not swModel Is Nothing Then
            
        Set swSelMgr = swModel.SelectionManager
        
        Dim swProfileSketch As SldWorks.Feature
        Set swProfileSketch = swModel.FeatureByName("Profile")
        
        Dim swBoundarySurface As SldWorks.Feature
        Set swBoundarySurface = swModel.FeatureByName("Boundary")
        
        Dim swDirectionSketch As SldWorks.Sketch
        Set swDirectionSketch = swModel.FeatureByName("Direction").GetSpecificFeature
        
        Dim swDirectionSeg As SldWorks.SketchSegment
        Set swDirectionSeg = swDirectionSketch.GetSketchSegments()(0)
        
        swSelMgr.SuspendSelectionList 'preserving current selections
        
        'selecting objects for extrude features (those selections won't be visible in the graphics view)
        AddToCurrentSelectionSet swProfileSketch, 0
        AddToCurrentSelectionSet swBoundarySurface, 1
        AddToCurrentSelectionSet swDirectionSeg, 16
        
        swModel.FeatureManager.FeatureExtrusion2 True, False, False, swEndConditions_e.swEndCondUpToSurface, 0, 0, 0, False, False, False, False, 0, 0, False, False, False, False, True, True, True, 0, 0, False

        'resuming the original selections
        swSelMgr.ResumeSelectionList
        
    Else
        MsgBox "Please open the sample model"
    End If

End Sub

Sub AddToCurrentSelectionSet(obj As Object, selMark As Integer)
    
    Dim swSelData As SldWorks.SelectData
    
    Set swSelData = swSelMgr.CreateSelectData
    
    swSelData.Mark = selMark
    
    swSelMgr.AddSelectionListObject obj, swSelData
    
End Sub
~~~

