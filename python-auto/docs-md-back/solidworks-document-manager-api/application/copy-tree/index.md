---
title: Copy documents tree using SOLIDWORKS Document Manager API
caption: Copy Documents Tree
description: Example demonstrates how to copy documents (assembly or drawing) tree to a new location by adding the suffix to each file preserving the references using SOLIDWORKS Document Manager API
image: copy-tree.png
labels: [copy tree, copy documents]
---
![SOLIDWORKS装配树已复制，并为每个文件添加了后缀](copy-tree.png){ width=350 }

本示例演示了如何使用SOLIDWORKS文档管理器API将装配或图纸树复制到新位置。宏允许为树中的每个文件添加后缀。宏将在装配的所有层级上保留并替换所有必需的引用。

在宏的开头的常量中指定要移动的输入文件、目标文件夹和后缀。

~~~ vb
Const FILE_PATH As String = "D:\Input\Assm1.SLDASM" '输入装配或图纸的完整路径
Const DEST_FOLDER As String = "D:\Output" '目标位置。文件夹路径末尾不要添加反斜杠'\'
Const SUFFIX As String = "_CodeStack" '要添加到树中每个文件的后缀
~~~

使用[ISwDMApplication::CopyDocument](https://help.solidworks.com/2018/english/api/swdocmgrapi/solidworks.interop.swdocumentmgr~solidworks.interop.swdocumentmgr.iswdmapplication~copydocument.html)文档管理器API来执行文件和所有引用的复制。

{% code-snippet { file-name: Macro.vba } %}