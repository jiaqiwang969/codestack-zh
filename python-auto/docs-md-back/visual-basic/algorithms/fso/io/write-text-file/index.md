---
title: Writing the text content into the file using Visual Basic (VBA)
caption: Write Text File
description: Function to write the text content into a file using Visual Basic (VBA) with an option to overwrite or append content.
labels: [write,text,output]
---
以下代码片段演示了如何使用Visual Basic（VBA）将文本写入指定的文件。该函数具有覆盖现有内容或追加内容的选项。

以下代码片段将覆盖目标文本文件中的数据

~~~ vb
WriteText("C:\MyFolder\MyFile.txt", "文本数据", False)
~~~

而以下代码片段将追加数据

~~~ vb
WriteText("C:\MyFolder\MyFile.txt", "文本数据", True)
~~~

如果文件不存在，代码将自动创建新文件。

如果出现任何错误（例如无法访问文件进行写入），将抛出异常。

{% code-snippet { file-name: WriteText.vba } %}