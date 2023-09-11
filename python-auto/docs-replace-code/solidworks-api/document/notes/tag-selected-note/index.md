---
title: Add Tag to selected note using SOLIDWORKS API
caption: Add Tag To Selected Note
description: Example demonstrates how to add text tag to the selected note in SOLIDWORKS model
image: drawing-note-revision.png
labels: [note, annotation. tag, attribute]
---
![在SOLIDWORKS图纸中带有修订号的注释](drawing-note-revision.png){ width=300 }

此示例演示了如何使用SOLIDWORKS API将文本标签（属性）添加到选定的注释中（零件、装配或图纸）。

在宏中将标签的名称指定为*TAG*常量。

* 标签允许跟踪模型会话中的特定注释。如果宏需要更新注释（例如更改修订版或链接值），这可能很有用。
* 如果注释更改其文本或格式，标签将被保留。
* 如果注释移动（包括从工作表空间移动到工作表格式），标签将被保留。
* 标签在用户界面上不可见/不可更改（只能通过SOLIDWORKS API访问）。

~~~ vb
Const TAG As String = "_CodeStackNote_"

Dim swApp As SldWorks.SldWorks

Sub main()

    Set swApp = Application.SldWorks
    
    Dim swModel As SldWorks.ModelDoc2
    
    Set swModel = swApp.ActiveDoc
    
    If Not swModel Is Nothing Then
        
        If Not TagSelectedNote(swModel, TAG) Then
            MsgBox "Failed to add tag to the note"
        End If
        
    Else
        MsgBox "Please open the model"
    End If
    
End Sub

Function TagSelectedNote(model As SldWorks.ModelDoc2, TAG As String) As Boolean
    
    On Error Resume Next
    
    Dim swSelMgr As SldWorks.SelectionMgr
    Set swSelMgr = model.SelectionManager
            
    Dim swNote As SldWorks.Note
    
    Set swNote = swSelMgr.GetSelectedObject6(1, -1)
    
    If Not swNote Is Nothing Then
        swNote.TagName = TAG
        TagSelectedNote = True
        Exit Function
    Else
        MsgBox "Please select note to add tag to"
    End If
    
    TagSelectedNote = False
    
End Function
~~~

