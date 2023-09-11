---
title: Read all invisible custom properties using SOLIDWORKS Document Manager API
caption: Read All Invisible Custom Properties
description: VBA example to read and output all invisible custom properties from the specific model using SOLIDWORKS Document Manager API
labels: [invisible, custom property]
---
SOLIDWORKS模型包含多个不可见的自定义属性，例如$PRP:"SW-文件名"，$PRP:"SW-标题"。这些属性是只读的，无法修改。

这个VBA宏使用SOLIDWORKS文档管理器API从指定模型中读取和输出所有不可见的自定义属性。结果以以下格式输出到VBA编辑器的即时窗口中：

~~~
...
SW-短日期: 12/09/2019 [文本]
SW-长日期: 星期四, 12 九月 2019 [文本]
SW-配置名称: A [文本]
...
SW-创建日期: 星期二, 10 九月 2019 10:46:55 上午 [文本]
SW-上次保存日期: 星期四, 12 九月 2019 8:33:04 下午 [文本]
SW-上次保存者: artem.taturevych [文本]
...
我的属性: 我的值 [文本]
~~~

在*FILE_PATH*常量中指定要读取属性的文件。

~~~ vb
Const SW_DM_KEY As String = "Your license key"

Const FILE_PATH As String = "C:\SampleModel.SLDPRT"

Dim swDmClassFactory As SwDocumentMgr.swDmClassFactory
Dim swDmApp As SwDocumentMgr.SwDMApplication

Sub main()

    Set swDmClassFactory = CreateObject("SwDocumentMgr.SwDMClassFactory")
    
    If Not swDmClassFactory Is Nothing Then
        
        Set swDmApp = swDmClassFactory.GetApplication(SW_DM_KEY)
        Dim swDmDoc As SwDocumentMgr.SwDMDocument19
        Set swDmDoc = OpenDocument(FILE_PATH, True)
        
        Dim vPrpNames As Variant
        vPrpNames = swDmDoc.GetInvisibleCustomPropertyNames()
        
        If Not IsEmpty(vPrpNames) Then
            
            Dim i As Integer
            
            For i = 0 To UBound(vPrpNames)
            
                Dim prpName As String
                prpName = vPrpNames(i)
                
                Dim prpType As SwDmCustomInfoType
            
                Dim prpTypeName As String
                
                Dim prpVal As String
                prpVal = swDmDoc.GetInvisibleCustomProperty(prpName, prpType)
                
                Select Case prpType
                    Case SwDmCustomInfoType.swDmCustomInfoDate
                        prpTypeName = "Date"
                    Case SwDmCustomInfoType.swDmCustomInfoNumber
                        prpTypeName = "Number"
                    Case SwDmCustomInfoType.swDmCustomInfoText
                        prpTypeName = "Text"
                    Case SwDmCustomInfoType.swDmCustomInfoYesOrNo
                        prpTypeName = "YesNo"
                    Case SwDmCustomInfoType.swDmCustomInfoUnknown
                        prpTypeName = "Unknown"
                End Select
            
                Debug.Print prpName & ": " & prpVal & " [" & prpTypeName & "]"
            Next
            
        End If
        
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

