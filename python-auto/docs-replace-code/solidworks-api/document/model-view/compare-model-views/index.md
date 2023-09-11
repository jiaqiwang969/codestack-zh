---
title: Compare model views transformations using SOLIDWORKS API
caption: Compare Model Views
description: Example demonstrates how to compare 2 model views (by orientation, translation and scale)
image: view-orientation.png
---
![模型视图方向](view-orientation.png){ width=250 }

这个示例演示了如何使用SOLIDWORKS API比较零件或装配中的两个模型视图。

宏将识别变化并显示结果，如果：

* 视图相同
* 视图方向不同（即旋转）
* 视图平移不同（即移动）
* 视图缩放不同

宏使用[用户定义类型](visual-basic/data-structures/types/) **ViewData** 来存储视图的方向、平移和缩放。这个结构与视图没有关联，表示视图变换的快照。

**CompareViewData** 函数的结果被定义为 *CompareViewResult_e* [标志枚举器](visual-basic/data-structures/enumerators#flag-enumerator-multiple-options)。这允许返回视图方向的特定变化或变化的组合。

* 打开模型并启动宏。
* 一旦读取了第一个视图的数据，宏将暂停执行。
* 更改视图并继续执行宏。
* 结果将显示在消息框中。

~~~ vb
Type ViewData
    ViewScale As Double
    Orientation As SldWorks.MathTransform
    Translation As SldWorks.MathVector
End Type

Enum CompareViewResult_e
    Same = 0
    DiffOrientation = 2 ^ 0
    DiffTranslation = 2 ^ 1
    DiffScale = 2 ^ 2
End Enum

Dim swApp As SldWorks.SldWorks

Sub main()

    Set swApp = Application.SldWorks
    
    Dim swModel As SldWorks.ModelDoc2
    
    Set swModel = swApp.ActiveDoc
    
    If Not swModel Is Nothing Then
        
        Dim swView As SldWorks.ModelView
        Set swView = swModel.ActiveView
        
        If Not swView Is Nothing Then
            
            Dim origViewData As ViewData
            origViewData = GetViewData(swView)
            
            Stop 'move the view now
            
            Dim newViewData As ViewData
            newViewData = GetViewData(swView)
            
            Dim compRes As CompareViewResult_e
            compRes = CompareViewData(origViewData, newViewData)
            
            If compRes = Same Then
                MsgBox "Views are the same"
            Else
                Dim msg As String
                
                If compRes And DiffOrientation Then
                    msg = msg & vbLf & "Orientation"
                End If
                
                If compRes And DiffTranslation Then
                    msg = msg & vbLf & "Translation"
                End If
                
                If compRes And DiffScale Then
                    msg = msg & vbLf & "Scale"
                End If
                
                MsgBox "Views are not the same. Differences:" & msg
                
            End If
            
        Else
            MsgBox "Please open part or assembly"
        End If
        
    Else
        MsgBox "Please open the model"
    End If
    
End Sub

Function GetViewData(view As SldWorks.ModelView) As ViewData
    
    Dim data As ViewData
    
    Set data.Orientation = view.Orientation3
    Set data.Translation = view.Translation3
    data.ViewScale = view.Scale2
    
    GetViewData = data
    
End Function

Function CompareViewData(firstViewData As ViewData, secondViewData As ViewData) As CompareViewResult_e
    
    Dim res As CompareViewResult_e
    res = Same
    
    If Not CompareArrays(firstViewData.Orientation.ArrayData, secondViewData.Orientation.ArrayData) Then
        res = res + DiffOrientation
    End If
    
    If Not CompareArrays(firstViewData.Translation.ArrayData, secondViewData.Translation.ArrayData) Then
        res = res + DiffTranslation
    End If
    
    If firstViewData.ViewScale <> secondViewData.ViewScale Then
        res = res + DiffScale
    End If
    
    CompareViewData = res
    
End Function

Function CompareArrays(firstArr As Variant, secondArr As Variant) As Boolean
    
    If UBound(firstArr) = UBound(secondArr) Then
        
        Dim i As Integer
        
        For i = 0 To UBound(firstArr)
            If firstArr(i) <> secondArr(i) Then
                CompareArrays = False
                Exit Function
            End If
        Next
        
        CompareArrays = True
    Else
        CompareArrays = False
    End If
    
End Function
~~~

