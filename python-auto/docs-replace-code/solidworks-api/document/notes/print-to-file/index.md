---
layout: sw-tool
title: Macro to print all notes to the text file from SOLIDWORKS drawing
caption: Print Notes Text To File
description: VBA macro to output all notes text to the text file from the SOLIDWORKS drawing file
image: print-notes.svg
labels: [note, print, regular expression, regex]
group: Drawing
---
这个VBA宏将从SOLIDWORKS图纸中的所有绘图视图中输出文本到文本文件中。

每个注释将在新行中打印。还可以在输出中包含视图和文件的名称。

## 配置

可以通过修改以下常量来配置宏

~~~ vb
Const FILE_PATH As String = "" '应写入注释的文本文件的完整路径。如果为空，则使用与原始文件相同的名称并添加_Note.txt前缀保存文件
Const PRINT_FILE_NAME As Boolean = True '如果为True，则将文件名输出到文本文件中
Const PRINT_VIEW_NAME As Boolean = True '如果为True，则将绘图视图名称输出到文本文件中
Const FILTER As String = "" '用于包含注释的正则表达式过滤器（例如，\d+表示包含所有包含数字值的注释）
~~~

## 注释

* 对于空注释，值将输出为**\[X\]**
* 有关可用于配置**FILTER**的正则表达式的更多信息，请参见[正则表达式](https://docs.microsoft.com/zh-cn/dotnet/standard/base-types/the-regular-expression-object-model)
* 注释将附加到现有的文本文件中（如果不存在，则创建新文件）。这允许通过[Batch+](https://cadplus.xarial.com/batch/)批量运行此宏以从多个文件中输出注释。

~~~ vb
Const FILE_PATH As String = ""
Const PRINT_FILE_NAME As Boolean = True
Const PRINT_VIEW_NAME As Boolean = True
Const FILTER As String = ""

Dim swApp As SldWorks.SldWorks

Sub main()

    Set swApp = Application.SldWorks
    
    Dim swDraw As SldWorks.DrawingDoc
    Set swDraw = swApp.ActiveDoc
    
    If Not swDraw Is Nothing Then
        
        Dim outFilePath As String
        
        If FILE_PATH <> "" Then
            outFilePath = FILE_PATH
        Else
            outFilePath = swDraw.GetPathName
            
            If outFilePath = "" Then
                Err.Raise "Drawing is not saved to the and FILE_PATH is not specified"
            End If
            
            outFilePath = Left(outFilePath, InStrRev(outFilePath, ".") - 1) & "_Notes.txt"
        End If
        
        Dim fileNmb As Integer
        fileNmb = FreeFile
    
        Open outFilePath For Append As #fileNmb
    
        If PRINT_FILE_NAME Then
            Print #fileNmb, "*** File Path: " & swDraw.GetPathName & " ***"
        End If
    
        PrintNotes swDraw, fileNmb
        
        Print #fileNmb, ""
        Close #fileNmb
        
    Else
        Err.Raise vbError, "", "Only drawings are supported"
    End If
    
End Sub

Sub PrintNotes(draw As SldWorks.DrawingDoc, fileNmb As Integer)
    
    Dim vSheets As Variant
    vSheets = draw.GetViews
    
    Dim i As Integer
        
    For i = 0 To UBound(vSheets)
        
        Dim vViews As Variant
        vViews = vSheets(i)
        
        Dim j As Integer
        
        For j = 0 To UBound(vViews)
            
            Dim swView As SldWorks.View
            Set swView = vViews(j)
            
            If PRINT_VIEW_NAME Then
                Print #fileNmb, "*** View Name: " & swView.Name & " ***"
            End If
            
            Dim vNotes As Variant
            vNotes = swView.GetNotes
            
            Dim k As Integer
            
            For k = 0 To UBound(vNotes)
                Dim swNote As SldWorks.Note
                Set swNote = vNotes(k)
                
                Dim text As String
                text = swNote.GetText
                
                If IncludeNote(text) Then
                    If text = "" Then
                        text = "[X]"
                    End If
                    
                    Print #fileNmb, text
                End If
                
            Next
            
        Next
        
    Next
    
End Sub

Function IncludeNote(text As String) As Boolean

    If FILTER = "" Then
        IncludeNote = True
    Else
        Dim regEx As Object
        Set regEx = CreateObject("VBScript.RegExp")
        
        regEx.Global = True
        regEx.IgnoreCase = True
        regEx.Pattern = FILTER
        
        IncludeNote = regEx.Test(text)
    
    End If
    
End Function
~~~

