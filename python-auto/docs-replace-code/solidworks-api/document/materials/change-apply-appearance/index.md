---
title: Change apply appearance option in material using SOLIDWORKS API
caption: Change Apply Appearance Option In Material
description: Example demonstrates how to change the Apply Appearance option in the material options
image: material-apply-appearance.png
labels: [part, solidworks api, material, appearance, example]
---
![编辑材料对话框中的应用外观选项](material-apply-appearance.png)

本示例演示了如何使用SOLIDWORKS API更改材料选项中的*应用外观*选项。

~~~ vb
Dim swApp As SldWorks.SldWorks
Dim swPart As SldWorks.PartDoc

Sub main()

    Set swApp = Application.SldWorks
    
    Set swPart = swApp.ActiveDoc
    
    If Not swPart Is Nothing Then
        
        Dim swMatVisPrps As SldWorks.MaterialVisualPropertiesData
        Set swMatVisPrps = swPart.GetMaterialVisualProperties
        swMatVisPrps.ApplyAppearance = False
        
        swPart.SetMaterialVisualProperties swMatVisPrps, swInConfigurationOpts_e.swAllConfiguration, Empty
    Else
        MsgBox "Please open part document"
    End If
    
End Sub
~~~

