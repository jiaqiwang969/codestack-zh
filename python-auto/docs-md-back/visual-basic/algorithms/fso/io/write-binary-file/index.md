---
title: Writing the binary content into the file using Visual Basic (VBA)
caption: Write Binary File
description: Function to write the binary content of byte array into a file using Visual Basic (VBA)
labels: [write,text,output]
---
以下代码片段演示了如何使用Visual Basic (VBA)将类型为*Byte()*的变量中的二进制数据写入指定的文件。

下面的代码片段将覆盖目标二进制文件中的数据。

~~~ vb
Dim arr(5237) As Byte
arr(0) = 12: arr(1) = 1: arr(2) = 0
...
WriteByteArrToFile("C:\MyFolder\MyFile.dat")
~~~

如果文件不存在，代码将自动创建新文件。

如果出现任何错误（例如无法访问文件进行写入），将抛出异常。

{% code-snippet { file-name: WriteBinary.vba } %}