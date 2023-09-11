---
layout: sw-tool
title: Copy component name to the component reference using SOLIDWORKS API
caption: Copy Component Name To Component Reference
description: VBA macro to copy component name to the component reference using SOLIDWORKS with an ability to filter virtual components only
image: component-reference.png
labels: [name,virtual,component reference]
group: Assembly
---
![组件引用](component-reference.png){ width=350 }

此VBA宏允许使用SOLIDWORKS API将活动装配中的组件名称复制到组件引用。

通过将*VIRTUAL_ONLY*选项设置为*True*，宏可以仅处理虚拟组件。

~~~ vb
Const VIRTUAL_ONLY As Boolean = True
~~~

如果组件名称用于存储项目属性（例如零件编号），则此宏可能很有用，因为组件名称无法添加到物料清单，而组件引用可以。

![带有组件引用的物料清单](bill-of-materials.png){ width=350 }

~~~ vb
Const VIRTUAL_ONLY As Boolean = False

Dim swApp As SldWorks.SldWorks

Sub main()
    
    Set swApp = Application.SldWorks
    
    Dim swModel As SldWorks.ModelDoc2
    Dim swSelMgr As SldWorks.SelectionMgr

    Set swModel = swApp.ActiveDoc
    
    If Not swModel Is Nothing Then
    
        If swModel.GetType() = swDocumentTypes_e.swDocASSEMBLY Then
        
            Dim swAssy As SldWorks.AssemblyDoc
            Set swAssy = swModel
            
            Dim vComps As Variant
            vComps = swAssy.GetComponents(False)
            
            Dim i As Integer
            
            For i = 0 To UBound(vComps)
                
                Dim swComp As SldWorks.Component2
                Set swComp = vComps(i)
                
                If swComp.IsVirtual Or Not VIRTUAL_ONLY Then
                
                    Dim compName As String
                    
                    compName = swComp.Name2
                    
                    If Not swComp.GetParent() Is Nothing Then
                        'if not root remove the sub-assemblies name
                        compName = Right(compName, Len(compName) - InStrRev(compName, "/"))
                    End If
                    
                    If swComp.IsVirtual() Then
                        'if virtual remove the context assembly name
                        compName = Left(compName, InStr(compName, "^") - 1)
                    Else
                        'remove the index name
                        compName = Left(compName, InStrRev(compName, "-") - 1)
                    End If
                    
                    swComp.ComponentReference = compName
                
                End If
                
            Next

        Else
            MsgBox "Active document is not an assembly"
        End If
    
    Else
        MsgBox "Please open assembly document"
    End If
    
End Sub
~~~

