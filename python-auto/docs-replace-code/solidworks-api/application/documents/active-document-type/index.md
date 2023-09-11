---
title: Determine the type Of active document using SOLIDWORKS API
caption: Determine The Type Of Active Document
description: Example displays the message box of the type of the document currently active in SOLIDWORKS
labels: [assembly, document, drawing, example, part, type]
redirect-from:
  - /2018/03/determine-type-of-active-document.html
---
该示例显示当前在SOLIDWORKS中活动文档的类型的消息框。无论文档是否已保存，此方法都适用。可以使用[IModelDoc2::GetType](https://help.solidworks.com/2018/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.IModelDoc2~GetType.html) SOLIDWORKS API方法返回类型枚举，以识别文档为SOLIDWORKS零件、装配或绘图。

~~~ vb
Dim swApp As SldWorks.SldWorks
Dim swModel As SldWorks.ModelDoc2

Sub main()

    Set swApp = Application.SldWorks
    
    Set swModel = swApp.ActiveDoc
    
    If Not swModel Is Nothing Then
        
        Select Case swModel.GetType
            
            Case swDocPART:
                MsgBox "Active document is Part"
            
            Case swDocASSEMBLY:
                MsgBox "Active document is Assembly"
                
            Case swDocDRAWING:
                MsgBox "Active document is Drawing"
        End Select
        
    Else
        
        MsgBox "No document opened"
        
    End If
    
End Sub
~~~

