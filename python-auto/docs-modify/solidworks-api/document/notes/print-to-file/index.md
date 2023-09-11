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

{% code-snippet { file-name: Macro.vba } %}