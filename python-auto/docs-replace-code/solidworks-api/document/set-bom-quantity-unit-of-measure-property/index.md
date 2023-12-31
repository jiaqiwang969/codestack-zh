---
title: Set BOM Quantity (Unit Of Measure) property using SOLIDWORKS API
caption: Set BOM Quantity (Unit Of Measure) Property In The Model
description: Example demonstrates how to modify the BOM quantity field in the properties dialog
image: bom-quantity-property.png
labels: [bom quantity, example, qty, unit of measure]
redirect-from:
  - /2018/03/set-bom-quantity-unit-of-measure.html
---
本示例演示了如何使用SOLIDWORKS API修改属性对话框中的BOM数量字段。

![指定与计量单位相关联的属性的选项](bom-quantity-property.png){ width=640 height=170 }

此选项允许覆盖BOM表中组件的数量值。

![显示修改后的组件数量的BOM表](bom-table-unit-of-measure.png){ width=640 }

要更改此属性，需要通过[SOLIDWORKS API接口ICustomPropertyManager](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.icustompropertymanager.html)设置隐藏的*UNIT_OF_MEASURE*自定义属性。

~~~ vb
Dim swApp As SldWorks.SldWorks
Dim swModel As SldWorks.ModelDoc2

Const BOM_QTY_PRP_NAME As String = "UNIT_OF_MEASURE"
Const QTY_PRP_NAME As String = "Qty"

Sub main()

    Set swApp = Application.SldWorks
    
    Set swModel = swApp.ActiveDoc
    
    If Not swModel Is Nothing Then
    
        Dim swCustPrpMgr As SldWorks.CustomPropertyManager
        
        Set swCustPrpMgr = swModel.Extension.CustomPropertyManager("")
            
        Dim bomQtyPrp As String
        swCustPrpMgr.Get3 BOM_QTY_PRP_NAME, False, "", bomQtyPrp
        
        Debug.Print bomQtyPrp
        
        swCustPrpMgr.Add2 BOM_QTY_PRP_NAME, swCustomInfoType_e.swCustomInfoText, QTY_PRP_NAME
        swCustPrpMgr.Set2 BOM_QTY_PRP_NAME, QTY_PRP_NAME
    
    Else
        
        MsgBox "Please open model"
        
    End If
    
End Sub
~~~

