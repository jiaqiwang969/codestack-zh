---
title: Reading the content of binary file using Visual Basic (VBA)
caption: Read Binary File
description: Reading the content of binary file into the byte array using Visual Basic (VBA)
labels: [read,input,binary]
---
以下代码片段演示了如何在Visual Basic 6 (VBA)中从指定文件中读取二进制内容到类型为 *Byte()* 的变量中。

~~~ vb
Dim content As Byte()
content = ReadByteArrFromFile("C:\MyFolder\MyFile.dat")
~~~

如果文件不存在或无法读取，代码将生成异常。

~~~ vb
Function ReadByteArrFromFile(filePath) As Byte()

    Dim buff() As Byte
    
    Dim fileNumb As Integer
    fileNumb = FreeFile
    
    Open filePath For Binary Access Read As fileNumb
    
    ReDim buff(0 To LOF(fileNumb) - 1)
    
    Get fileNumb, , buff
    
    Close fileNumb
    
    ReadByteArrFromFile = buff
    
End Function
~~~

