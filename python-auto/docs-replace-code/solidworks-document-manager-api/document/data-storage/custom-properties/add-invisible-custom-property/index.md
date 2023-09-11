---
title: Add invisible custom property to the model using SOLIDWORKS Document Manager API
caption: Add Invisible Custom Property
description: VBA macro to add invisible custom property to the model using SOLIDWORKS Document Manager API
labels: [invisible, custom property]
---
SOLIDWORKS 模型包含几个不可见的自定义属性，例如 $PRP:"SW-文件名"，$PRP:"SW-标题"。这些属性是只读的，无法从用户界面进行修改。但是，可以使用 Document Manager API 添加新的自定义属性。该属性在自定义属性管理器页面不可用，用户或 SOLIDWORKS API 无法修改。

此 VBA 示例演示了如何为指定的模型添加不可见的自定义属性。请按照以下方式配置宏：

~~~ vb
Const FILE_PATH As String = "C:\SampleModel.SLDPRT" '要添加不可见属性的文件的完整路径
Const PRP_NAME As String = "MyProperty" '要添加的属性名称
Const PRP_VAL As String = "MyValue" '要分配的属性值
~~~

~~~ vb
Const SW_DM_KEY As String = "Your license"

Const FILE_PATH As String = "C:\SampleModel.SLDPRT"
Const PRP_NAME As String = "MyProperty"
Const PRP_VAL As String = "MyValue"

Dim swDmClassFactory As SwDocumentMgr.swDmClassFactory
Dim swDmApp As SwDocumentMgr.SwDMApplication

Sub main()

    Set swDmClassFactory = CreateObject("SwDocumentMgr.SwDMClassFactory")
    
    If Not swDmClassFactory Is Nothing Then
        
        Set swDmApp = swDmClassFactory.GetApplication(SW_DM_KEY)
        Dim swDmDoc As SwDocumentMgr.SwDMDocument19
        Set swDmDoc = OpenDocument(FILE_PATH, False)
        
        swDmDoc.AddInvisibleCustomProperty PRP_NAME, SwDmCustomInfoType.swDmCustomInfoText, PRP_VAL
        swDmDoc.SetInvisibleCustomProperty PRP_NAME, PRP_VAL
        
        swDmDoc.Save
        swDmDoc.CloseDoc
        
    Else
        MsgBox "Document Manager SDK is not installed"
    End If
    
End Sub

Function OpenDocument(filePath As String, readOnly As Boolean) As SwDocumentMgr.SwDMDocument19
    
    Dim openErr As SwDmDocumentOpenError
    
    Dim docType As SwDocumentMgr.SwDmDocumentType
    
    Dim ext As String
    ext = LCase(Right(filePath, Len(".SLDXXX")))
    
    Select Case ext
        Case ".sldprt"
            docType = swDmDocumentPart
        Case ".sldasm"
            docType = swDmDocumentAssembly
        Case ".slddrw"
            docType = swDmDocumentDrawing
    End Select
    
    Dim swDmDoc As SwDocumentMgr.SwDMDocument19
    
    Set swDmDoc = swDmApp.GetDocument(filePath, docType, readOnly, openErr)
    
    If swDmDoc Is Nothing Then
        Err.Raise vbError, "", "Failed to open document: " & openErr
    End If
    
    Set OpenDocument = swDmDoc
    
End Function
~~~

