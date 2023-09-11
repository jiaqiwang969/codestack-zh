---
title: Get instance Id of assembly component using SOLIDWORKS API
caption: Get Instance Id Of Component
description: Example extracts the component instance index from the component's name
image: sw-component-properties.png
labels: [assembly, component, example, instance id, solidworks api]
redirect-from:
  - /2018/03/solidworks-api-assembly-get-component-instance-id.html
  - /solidworks-api/document/assembly/get-component-instance-id
---
该示例使用SOLIDWORKS API从组件的名称中提取组件实例索引。

![组件属性对话框中的组件实例ID选项](sw-component-properties.png){ width=400 }

~~~ vb
Dim swApp As SldWorks.SldWorks
Dim swModel As SldWorks.ModelDoc2
Dim swSelMgr As SldWorks.SelectionMgr
Dim swComp As SldWorks.Component2

Sub main()

    Set swApp = Application.SldWorks

    Set swModel = swApp.ActiveDoc
    
    If Not swModel Is Nothing Then
    
        Set swSelMgr = swModel.SelectionManager
        
        Set swComp = swSelMgr.GetSelectedObjectsComponent3(1, -1)
        
        If Not swComp Is Nothing Then
        
            Dim instId As Integer
            Dim compName As String
            compName = swComp.Name2
            instId = CInt(Right(compName, Len(compName) - InStrRev(compName, "-")))
            
            MsgBox "Selected component's instance id is " & instId
                
        Else
            
            MsgBox "Please select component"
            
        End If
        
    Else
        
        MsgBox "Please open assembly"
        
    End If
    
End Sub


~~~

