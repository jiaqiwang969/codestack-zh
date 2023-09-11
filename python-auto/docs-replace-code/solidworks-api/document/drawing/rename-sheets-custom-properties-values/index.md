---
layout: sw-tool
title: Rename SOLIDWORKS drawing sheets with custom properties values
caption: Rename Drawing Sheets With Custom Properties Values
description: Macro will rename all drawings sheets using the value of the specified custom property using SOLIDWORKS API
image: drw-sheets.png
labels: [custom property, drawing, example, macro, properties, rename, sheet, solidworks api, vba]
group: Drawing
redirect-from:
  - /2018/03/document_8.html
---
该宏将使用SOLIDWORKS API根据指定的自定义属性值重命名所有图纸工作表。

![图纸中的工作表列表](drw-sheets.png){ width=320 }

* 打开图纸并运行宏
* 指定要读取值的属性

![输入属性名称的弹出窗口](get-prp-name.png){ width=320 }

* 所有工作表将根据此属性的值进行重命名。宏将从工作表属性中指定的模型视图中获取该值。
不支持“与文档属性中指定的工作表相同”的选项。
如果选择了此选项，则将使用第一个视图的属性。
宏将尝试读取配置特定的属性，如果未指定属性，则读取模型级属性。

![在工作表属性中使用模型的自定义属性值选项](use-custom-prps-from-view-sheet-property.png){ width=400 }

~~~ vb
Dim swApp As SldWorks.SldWorks
Dim swDraw As SldWorks.DrawingDoc

Sub main()

    Set swApp = Application.SldWorks
    
    Set swDraw = swApp.ActiveDoc
    
    If swDraw Is Nothing Then
        MsgBox "Please open the drawing"
        End
    End If
    
    Dim prpName As String
    prpName = InputBox("Please specify the custom property name to get the value from")
    
    Dim vSheetNames As Variant
    vSheetNames = swDraw.GetSheetNames
    
    Dim i As Integer
    
    For i = 0 To UBound(vSheetNames)
        
        Dim swSheet As SldWorks.Sheet
        Set swSheet = swDraw.Sheet(vSheetNames(i))
        
        Dim custPrpViewName As String
        custPrpViewName = swSheet.CustomPropertyView
        
        Dim vViews As Variant
        vViews = swSheet.GetViews()
        
        Dim swCustPrpView As SldWorks.View
        Set swCustPrpView = Nothing
        
        Dim j As Integer
        
        For j = 0 To UBound(vViews)
            
            Dim swView As SldWorks.View
            Set swView = vViews(j)
            
            If LCase(swView.Name) = LCase(custPrpViewName) Then
                Set swCustPrpView = swView
                Exit For
            End If
            
        Next
        
        If swCustPrpView Is Nothing Then
            Set swCustPrpView = vViews(0)
        End If
        
        If Not swCustPrpView Is Nothing Then
            
            Dim swRefConfName As String
            Dim swRefDoc As SldWorks.ModelDoc2
            
            swRefConfName = swCustPrpView.ReferencedConfiguration
            Set swRefDoc = swCustPrpView.ReferencedDocument
            
            If Not swRefDoc Is Nothing Then
                
                Dim prpValue As String
                
                prpValue = GetCustomPropertyValue(swRefDoc, swRefConfName, prpName)
                
                If prpValue <> "" Then
                    swSheet.SetName (prpValue)
                End If
                
            Else
                MsgBox "Failed to get the model from drawing view. Make sure that the drawing is not lightweight"
            End If
            
        Else
            MsgBox "Failed to get the view to get property from"
        End If
        
    Next
    
End Sub

Function GetCustomPropertyValue(model as SldWorks.ModelDoc2, confName as String, prpName As String) As String
    
    Dim prpValue As String
                
    model.Extension.CustomPropertyManager(confName).Get3 prpName, False, "", prpValue
    
    If prpValue = "" Then
        model.Extension.CustomPropertyManager("").Get3 prpName, False, "", prpValue
    End If
    
    GetCustomPropertyValue = prpValue
    
End Function
~~~

