---
title: Reading the content of text file using Visual Basic (VBA)
caption: Read Text File
description: Reading the content of text file into the variable using Visual Basic (VBA)
labels: [read,input]
---
以下代码片段演示了如何从指定的文件中读取文本内容。

~~~ vb
Dim content As String
content = ReadText("C:\MyFolder\MyFile.txt")
~~~

如果文件不存在或无法读取，代码将生成异常。

~~~ vb
Function ReadText(filePath As String) As String
    
    Dim fileNo As Integer

    fileNo = FreeFile
    
    Dim content As String
    
    Dim isFirstLine As Integer
    isFirstLine = True
    
    Open filePath For Input As #fileNo
    
    Do While Not EOF(fileNo)
        
        Dim line As String
        
        Line Input #fileNo, line
        
        content = content & IIf(Not isFirstLine, vbLf, "") & line
        isFirstLine = False
        
    Loop
    
    Close #fileNo
    
    ReadText = content
    
End Function
~~~

