---
layout: sw-tool
title: Sort file and configuration specific custom properties using SOLIDWORKS API
caption: Sort Custom Properties
description: VBA macro to sort file and configuration specific custom properties (in ascending and descending order) using logical order via SOLIDWORKS API
image: sort-custom-properties.svg
labels: [sort, custom properties, bubble]
group: Custom Properties
---
![排序后的自定义属性](sorted-custom-properties.png){ width=350 }

这个VBA宏使用SOLIDWORKS API按照逻辑顺序对文件和所有配置的自定义属性进行排序。可以指定升序和降序排序。

逻辑顺序按照以下方式对元素进行排序。这是Windows文件资源管理器中文件的排序顺序：

* 属性1
* 属性2
* 属性3
* 属性12
* 属性20
* 属性21
* 属性30

而对于上述序列的字母排序将产生以下结果：

* 属性1
* 属性12
* 属性2
* 属性20
* 属性21
* 属性3
* 属性30

## 配置

可以通过更改宏中的常量值来配置宏，如下所示：

~~~ vb
Const ASCENDING As Boolean = True 'True表示升序排序，False表示降序排序
Const REORDER_GENERAL_CUST_PRPS As Boolean = True 'True表示对文件特定的自定义属性进行排序，False表示跳过
Const REORDER_CONF_CUST_PRPS As Boolean = True 'True表示对配置特定的自定义属性进行排序（对于零件和装配体），False表示跳过
~~~

观看[演示视频](https://youtu.be/jsjN8zNRTuc?t=97)

~~~ vb
Declare PtrSafe Function StrCmpLogicalW Lib "shlwapi" (ByVal s1 As String, ByVal s2 As String) As Integer

Const ASCENDING As Boolean = True
Const REORDER_GENERAL_CUST_PRPS As Boolean = True
Const REORDER_CONF_CUST_PRPS As Boolean = True

Dim swApp As SldWorks.SldWorks

Sub main()

    Set swApp = Application.SldWorks
    
    Dim swModel As SldWorks.ModelDoc2
    
    Set swModel = swApp.ActiveDoc
    
    If Not swModel Is Nothing Then
                
        If REORDER_GENERAL_CUST_PRPS Then
            Dim swCustPrpMgr As SldWorks.CustomPropertyManager
            Set swCustPrpMgr = swModel.Extension.CustomPropertyManager("")
            ReorderProperties swCustPrpMgr, ASCENDING
        End If
        
        If REORDER_CONF_CUST_PRPS Then
            
            Dim vConfNames As Variant
            vConfNames = swModel.GetConfigurationNames
            
            If Not IsEmpty(vConfNames) Then
                
                Dim i As Integer
                
                For i = 0 To UBound(vConfNames)
                    Dim swConfCustPrpMgr As SldWorks.CustomPropertyManager
                    Set swConfCustPrpMgr = swModel.Extension.CustomPropertyManager(vConfNames(i))
                    ReorderProperties swConfCustPrpMgr, ASCENDING
                Next
                
            End If
            
        End If
        
        swModel.SetSaveFlag
        
    Else
        MsgBox "Please open document"
        
    End If
        
End Sub

Sub ReorderProperties(custPrpMgr As SldWorks.CustomPropertyManager, asc As Boolean)
    
    Dim vPrpNames As Variant
    Dim vPrpTypes As Variant
    
    'NOTE: returned properties values are resolved for both valOut and resValOut parameters
    custPrpMgr.GetAll2 vPrpNames, vPrpTypes, Empty, Empty
    
    If Not IsEmpty(vPrpNames) Then
    
        Dim dict As Object
        Set dict = CreateObject("Scripting.Dictionary")
        
        Dim i As Integer
        
        For i = 0 To UBound(vPrpNames)
            Dim prpVal As String
            custPrpMgr.Get3 vPrpNames(i), False, prpVal, ""
            dict.Add vPrpNames(i), Array(vPrpTypes(i), prpVal)
            custPrpMgr.Delete2 vPrpNames(i)
        Next
    
        vPrpNames = BubbleSort(vPrpNames, asc)
        
        For i = 0 To UBound(vPrpNames)
            Dim vPrpData As Variant
            vPrpData = dict.Item(vPrpNames(i))
            If custPrpMgr.Add3(vPrpNames(i), vPrpData(0), vPrpData(1), swCustomPropertyAddOption_e.swCustomPropertyOnlyIfNew) <> swCustomInfoAddResult_e.swCustomInfoAddResult_AddedOrChanged Then
                Err.Raise vbError, "", "Failed to add property"
            End If
        Next
        
    End If
End Sub

Function BubbleSort(vStrArray As Variant, asc As Boolean) As Variant
    
    Dim swapPos As Integer
    swapPos = IIf(asc, 1, -1)
    
    Dim vResStrArray As Variant
    vResStrArray = vStrArray
    
    Dim i As Integer
    Dim j As Integer
    Dim tempVal As String
    
    For i = 0 To UBound(vResStrArray)
        For j = i To UBound(vResStrArray)
            If StrCmpLogicalW(StrConv(CStr(vResStrArray(i)), vbUnicode), StrConv(CStr(vResStrArray(j)), vbUnicode)) = swapPos Then
                tempVal = vResStrArray(j)
                vResStrArray(j) = vResStrArray(i)
                vResStrArray(i) = tempVal
            End If
        Next
    Next
    
    BubbleSort = vResStrArray
    
End Function
~~~

