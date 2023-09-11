---
caption: Traverse Feature Tree Reversed
title: Traverse SOLIDWORKS feature manager tree in the reversed order
description: VBA macro to traverse feature manager tree in SOLIDWORKS document in the reversed order
---

这个VBA宏演示了如何反向遍历活动SOLIDWORKS文档的特征管理器树。

~~~ vb
Dim swApp As SldWorks.SldWorks

Sub main()

    Set swApp = Application.SldWorks
    
    Dim swModel As SldWorks.ModelDoc2
    
    Set swModel = swApp.ActiveDoc
    
    Dim i As Integer
    
    i = 0
    
    Dim swFeat As SldWorks.Feature
    
    Do
        
        Set swFeat = swModel.FeatureByPositionReverse(i)
        i = i + 1
        
        If Not swFeat Is Nothing Then
            Debug.Print swFeat.Name
        End If
        
    Loop While Not swFeat Is Nothing
    
End Sub
~~~

