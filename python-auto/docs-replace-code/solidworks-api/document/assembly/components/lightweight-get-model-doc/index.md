---
title: Get Model Doc from lightweight component using SOLIDWORKS API
caption: Get Model Doc From Lightweight Component
description: Example demonstrates how to get the pointer to IModelDoc2 from the component (even if it is in the suppressed or lightweight state)
image: lightweight-component.png
labels: [assembly, component, example, lightweight, modeldoc, memory, solidworks api]
---
![装配树中的轻量级组件](lightweight-component.png)

[IComponent2::GetModelDoc2](https://help.solidworks.com/2012/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IComponent2~GetModelDoc2.html) 是SOLIDWORKS API的方法，它返回指向[IModelDoc2](https://help.solidworks.com/2012/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IModelDoc2.html)接口的指针。

需要使用该接口来检索模型特定信息（如自定义属性、特征树、注释等）。

对于以轻量级或抑制状态加载的组件，模型文档是不可用的（即指针为*NULL*）。

以下示例演示了如何使用SOLIDWORKS API从组件中获取到IModelDoc2指针（即使组件处于抑制或轻量级状态）。通过直接将组件加载到内存中，无需解析组件或在其自己的窗口中打开文件，即可实现该结果。

~~~ vb
Dim swApp As SldWorks.SldWorks
Dim swAssy As SldWorks.AssemblyDoc

Sub main()

    On Error Resume Next
    
    Set swApp = Application.SldWorks
    
    Set swAssy = swApp.ActiveDoc
    
    If Not swAssy Is Nothing Then
        
        Dim swComp As SldWorks.Component2
        Set swComp = swAssy.SelectionManager.GetSelectedObject6(1, -1)
        
        If Not swComp Is Nothing Then
        
            Dim swRefModel As SldWorks.ModelDoc2
            Set swRefModel = GetModelDocFromComponent(swComp)
            
            Debug.Print swRefModel.GetTitle
            
        Else
            MsgBox "Please select the component"
        End If
        
    Else
        MsgBox "Please open assembly"
    End If
    
End Sub

Function GetModelDocFromComponent(comp As SldWorks.Component2) As SldWorks.ModelDoc2
    
    Dim swRefModel As SldWorks.ModelDoc2
    Set swRefModel = comp.GetModelDoc2
    
    If swRefModel Is Nothing Then 'component is lightweight or suppressed
        
        Dim path As String
        path = comp.GetPathName
        
        Dim docType As swDocumentTypes_e
        
        docType = GetDocumentTypeFromPath(path)
        
        On Error GoTo End_
        
        swApp.DocumentVisible False, docType
        
        Dim errs As Long
        Dim wrns As Long
        Set swRefModel = swApp.OpenDoc6(path, docType, swOpenDocOptions_e.swOpenDocOptions_Silent, "", errs, wrns)
        
End_: 'restore the flag otherwise all files will be opened invisible
    swApp.DocumentVisible True, docType
        
    End If
    
    Set GetModelDocFromComponent = swRefModel

End Function

Function GetDocumentTypeFromPath(path As String) As swDocumentTypes_e
    
    Dim ext As String
    ext = Right(path, Len(path) - InStrRev(path, "."))
    
    Select Case UCase(ext)
        
        Case "SLDPRT"
            GetDocumentTypeFromPath = swDocPART
            Exit Function
            
        Case "SLDASM"
            GetDocumentTypeFromPath = swDocASSEMBLY
            Exit Function
            
        Case "SLDDRW"
            GetDocumentTypeFromPath = swDocDRAWING
            Exit Function
            
    End Select
    
End Function
~~~

