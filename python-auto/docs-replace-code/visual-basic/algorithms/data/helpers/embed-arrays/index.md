---
title: Embed Array In Visual Basic 6 (VBA) code
caption: Embed Arrays
description: Workarounds for embedding data in array within the Visual Basic 6 (VBA) project
image: array-text-declaration.png
labels: [embed array,declare array]
---
在某些情况下，可能需要直接将文件或数据嵌入到Visual Basic 6项目或VBA宏中。Visual Basic不支持资源。下面的函数演示了如何将二进制数组嵌入到宏中，而无需重新分发数据文件。

## 编写数组声明

此选项允许将数组声明输出为文本格式，可以将其复制粘贴到宏中作为变量声明。

~~~vb
Dim buff(5) As Byte
buff(0) = 1: buff(1) = 2: buff(2) = 3
buff(3) = 4: buff(4) = 5: buff(5) = 6

WriteArrayDeclarationToFile buff, "D:\arr.txt", "arr", "Byte", 2
~~~

只需复制生成文件的内容并粘贴到宏模块中即可嵌入数据。

![以文本形式声明的数组](array-text-declaration.png)

~~~ vb
Sub WriteArrayDeclarationToFile(buffer As Variant, filePath As String, varName As String, typeName As String, Optional elemsPerRow As Integer = 10)
    
    Dim fileNo As Integer
    fileNo = FreeFile
    
    Open filePath For Output As #fileNo
    
    Print #fileNo, "Dim " & varName & "(" & UBound(buffer) & ") As " & typeName
    
    Dim i As Long
    
    For i = 0 To UBound(buffer) Step elemsPerRow
        
        Dim j As Long
        Dim last As Long
        
        If i + elemsPerRow > UBound(buffer) Then
            last = UBound(buffer)
        Else
            last = i + elemsPerRow - 1
        End If
        
        Dim line As String
        line = ""
        
        For j = i To last
            Dim val As String
            val = buffer(j)
            If LCase(typeName) = "string" Then
                val = """" & val & """"
            End If
            line = IIf(line <> "", line & ": ", "") + varName & "(" & j & ")=" & val
        Next
        
        Print #fileNo, line
        
    Next
    
    Close #fileNo
    
End Sub
~~~



然而，这种方法有一个限制，即文件的大小将比数组的大小大得多（例如，大小为500 KB的数组将生成约10 MB的文件）。这会导致Visual Basic中的“内存不足”错误。

![VBA中的内存不足错误](vba-out-of-memory-error.png)

## 编写Base64编码的数组

作为解决方法，可以将数组嵌入为Base64字符串。请参考以下文章中的代码示例，了解如何将字节数组编码为Base64字符串：[将字节数组编码为Base64字符串](/visual-basic/algorithms/data/encoding/base64#encode)

~~~vb
Dim buff(100) As Byte
...
WriteByteArrayDeclarationToFileAsBase64 buff, "D:\arr1.txt"
~~~

这将创建以下文件：

![Base64编码的数组](array-base64-encoded.png){ width=350 }

声明字符串常量并将值从此文件中粘贴。[解码](/visual-basic/algorithms/data/encoding/base64#decode)此字符串以获取字节数组。

此解决方案也可能遇到每行的最大符号数限制。

![VBA中的行长度限制](vba-line-length-limitation.png)

为了解决这个问题，使用*WriteByteArrayDeclarationToFileAsBase64*方法的第三个参数，它允许设置最大符号数，并自动使用行继续符号拆分行：

~~~vb
WriteByteArrayDeclarationToFileAsBase64 buff, "D:\arr1.txt", 100
~~~

该函数提供了解决每行最大继续数限制（等于24个，“行继续过多”）并将数据拆分为不同函数的方法。

![VBA中的行继续过多错误](too-many-line-continuations.png)

结果，数据以以下格式写入文件：

![由函数拆分的Base64编码字符串](vba-array-split-by-functions.png){ width=350 }

要使用此方法，将内容复制到模块中，并从代码中调用*GetBase64Buffer*函数，该函数将返回Base64编码的数组，可以进行[解码](/visual-basic/algorithms/data/encoding/base64#decode)。

~~~ vb
Sub WriteByteArrayDeclarationToFileAsBase64(buffer As Variant, filePath As String, Optional lineMaxLength As Integer = -1)
    
    Const FUNC_NAME = "GetBufferPart"
    
    Dim fileNo As Integer
    fileNo = FreeFile
    
    Open filePath For Output As #fileNo
        
    Dim data As String
    data = ConvertToBase64String(buffer)
    data = Replace(data, vbLf, "")
    
    If lineMaxLength > 1 Then
            
        Const MAX_LINE_CONTINUATIONS As Integer = 24
        
        Dim curLineIndex As Integer
        Dim curCont As Integer
        curLineIndex = 0
        
        Dim i As Long
        
        Dim funcsCount As Integer
        funcsCount = Round((Len(data) - 1) / lineMaxLength / MAX_LINE_CONTINUATIONS) - 1
        
        Print #fileNo, "Function GetBase64Buffer() As String"
                
        For i = 0 To funcsCount
            Print #fileNo, "GetBase64Buffer = GetBase64Buffer & " & FUNC_NAME & i & "()"
        Next
        
        Print #fileNo, "End Function"
        
        Dim funcName As String
        
        For i = 1 To Len(data) Step lineMaxLength
            
            If curCont = MAX_LINE_CONTINUATIONS Then
                curCont = 0
                curLineIndex = curLineIndex + 1
            End If
            
            Dim length As Integer
        
            Dim isLast As Boolean
            isLast = False
            
            If i + lineMaxLength > Len(data) Then
                length = Len(data) - i + 1
                isLast = True
            Else
                length = lineMaxLength
            End If
            
            curCont = curCont + 1
            
            If curCont = 1 Then
                funcName = FUNC_NAME & curLineIndex
                Print #fileNo, "Function " & funcName & "() As String"
            End If
            
            isLast = isLast Or curCont >= MAX_LINE_CONTINUATIONS
            
            Dim lineConc As String
            lineConc = ""
            If Not isLast Then
                lineConc = " & _"
            End If
            
            Print #fileNo, IIf(curCont = 1, funcName & " = ", ""); """" & Mid(data, i, length) & """" & lineConc
            
            If isLast Then
                Print #fileNo, "End Function"
            End If
            
        Next
        
    Else
        Print #fileNo, data
    End If
    
    Close #fileNo
    
End Sub

Function ConvertToBase64String(vArr As Variant) As String
    
    Dim xmlDoc As Object
    Dim xmlNode As Object
    
    Set xmlDoc = CreateObject("MSXML2.DOMDocument")
    
    Set xmlNode = xmlDoc.createElement("b64")
    
    xmlNode.DataType = "bin.base64"
    xmlNode.nodeTypedValue = vArr
    
    ConvertToBase64String = xmlNode.Text
    
End Function
~~~

