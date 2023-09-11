---
title: 使用Visual Basic (VBA)读取文本文件内容
caption: 读取文本文件
description: 使用Visual Basic (VBA)将文本文件内容读取到变量中
labels: [读取, 输入]
---
以下代码片段演示了如何从指定的文件中读取文本内容。

~~~ vb
Dim content As String
content = ReadText("C:\MyFolder\MyFile.txt")
~~~

如果文件不存在或无法读取，代码将生成异常。

{% code-snippet { file-name: ReadText.vba } %}