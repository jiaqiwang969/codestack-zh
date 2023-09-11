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

{% code-snippet { file-name: ReadText.vba } %}