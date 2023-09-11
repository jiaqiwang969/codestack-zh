---
title: Read table content into array using SOLIDWORKS API
caption: Read Table Content Into Array
description: Example demonstrates how to read the content of the selected table (Bill Of Materials, General Table, Cut-List Table etc.) into the 2-dimensional array
labels: [array, bom, read, solidworks api, table]
redirect-from:
  - /2018/03/solidworks-api-model-read-table-content-into-array.html
---
本示例演示了如何使用SOLIDWORKS API将选定表格（物料清单、常规表格、切割清单表格等）的内容读入二维数组中。

[SOLIDWORKS API接口ITableAnnotation](https://help.solidworks.com/2018/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.ITableAnnotation.html)提供了访问所有表格类型数据的功能。

~~~ vb
Dim swApp As SldWorks.SldWorks
Dim swModel As SldWorks.ModelDoc2
Dim swSelMgr As SldWorks.SelectionMgr
Dim swTableAnnotation As SldWorks.TableAnnotation

Sub main()

    Set swApp = Application.SldWorks
    
    Set swModel = swApp.ActiveDoc
    
    If Not swModel Is Nothing Then

        Set swSelMgr = swModel.SelectionManager
        
        Dim tableData() As String
        
        Set swTableAnnotation = swSelMgr.GetSelectedObject6(1, -1)
        
        If Not swTableAnnotation Is Nothing Then
            
            ReDim tableData(swTableAnnotation.RowCount - 1, swTableAnnotation.ColumnCount - 1)
            
            Dim i As Integer
            Dim j As Integer
            
            For i = 0 To swTableAnnotation.RowCount - 1
                
                For j = 0 To swTableAnnotation.ColumnCount - 1
                    tableData(i, j) = swTableAnnotation.Text(i, j)
                Next
                
            Next
        Else
            MsgBox "Please select table"
        End If
    Else
        MsgBox "Please open model"
    End If
End Sub

~~~

