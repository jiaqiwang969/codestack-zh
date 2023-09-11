---
caption: Report File Versions
title: Generate report for the SOLIDWORKS file versions (created and last saved) for all the files in the folder
description: VBA macro which generates CSV report of versions (created and last saved) for all files in the folder
image: solidworks-file-versions-report.png
---
![SOLIDWORKS文件版本报告](solidworks-file-versions-report.png) { width=500 }

这个VBA宏会在指定的文件夹中生成一个CSV报告（可以在Excel中打开），报告包含了SOLIDWORKS文件的创建和最后保存的版本信息。

> 这个宏不会逐个打开每个模型，从而大大减少了处理时间。

可以通过修改下面的常量来配置宏的输入和输出参数。

~~~ vb
Const INPUT_FOLDER_PATH As String = "D:\MyModels" 'SOLIDWORKS文件所在文件夹的完整路径
Const OUT_FILE_PATH As String = "D:\sw-file-versions.csv" '报告的输出CSV文件的完整路径
Const FILES_FILTER As String = "*.sld*" '文件过滤器，支持通配符
Const INCLUDE_SUB_FOLDERS As Boolean = True 'True表示处理子文件夹，False表示只处理顶层文件
~~~

{% code-snippet { file-name: Macro.vba } %}