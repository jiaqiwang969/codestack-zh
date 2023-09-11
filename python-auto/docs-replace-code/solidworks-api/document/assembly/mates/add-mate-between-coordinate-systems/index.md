---
title: Add mate between coordinate systems using SOLIDWORKS API
caption: Add Mate Between Coordinate Systems
description: Macro adds coincident mate between 2 coordinate systems of 2 selected components
image: sw-mate-coincident.png
labels: [assembly, component, coordinate system, example, mate, solidworks api]
redirect-from:
  - /2018/03/solidworks-api-assembly-add-mate-between-coord-sys.html
  - /solidworks-api/document/assembly/add-mate-between-coordinate-systems
---
使用SOLIDWORKS API在两个选定的组件的两个坐标系之间添加一致连接。这些组件必须包含名为*Coordinate System1*的坐标系特征。

![一致连接属性管理器页面](sw-mate-coincident.png){ width=640 }

使用[IAssemblyDoc::AddMate3](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.iassemblydoc~addmate3.html) SOLIDWORKS API插入连接特征。

~~~ vb
Dim swApp As SldWorks.SldWorks
Dim swAssy As SldWorks.AssemblyDoc
Dim swSelMgr As SldWorks.SelectionMgr

Sub main()

    Set swApp = Application.SldWorks
    
    Set swAssy = swApp.ActiveDoc
        
    If Not swAssy Is Nothing Then
    
        Set swSelMgr = swAssy.SelectionManager
                
        Dim swCs1 As SldWorks.Feature
        Dim swCs2 As SldWorks.Feature
    
        Set swCs1 = GetCoordinateSystemFromSelection(1, "Coordinate System1")
        Set swCs2 = GetCoordinateSystemFromSelection(2, "Coordinate System1")
        
        swCs1.Select2 False, 1
        swCs2.Select2 True, 1
        
        swAssy.AddMate3 swMateType_e.swMateCOINCIDENT, swMateAlign_e.swMateAlignCLOSEST, False, 0, 0, 0, 0, 0, 0, 0, 0, False, 0
        
        swAssy.EditRebuild
    
    Else
        
        MsgBox "Please open assembly"
    
    End If
    
End Sub

Function GetCoordinateSystemFromSelection(index As Integer, name As String) As SldWorks.Feature
    
    Dim swComp As SldWorks.Component2
    Dim swCoordSys As SldWorks.Feature
    
    Set swComp = swSelMgr.GetSelectedObjectsComponent2(index)
    
    If Not swComp Is Nothing Then
    
        Set swCoordSys = swComp.FeatureByName(name)
        
        If swCoordSys Is Nothing Then
            MsgBox "Component " & swComp.Name2 & " doesn't contain the feature " & name
            End
        End If
    
    Else
        
        MsgBox "Please select 2 components"
        End
        
    End If
    
    Set GetCoordinateSystemFromSelection = swCoordSys
    
End Function


~~~

