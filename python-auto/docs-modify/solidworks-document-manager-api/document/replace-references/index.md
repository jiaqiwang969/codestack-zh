---
title: Replace references in components or drawing views using SOLIDWORKS Document Manager API
caption: Replace References
description: Example demonstrates how to replace references (components or drawing views) in SOLIDWORKS files using Document Manager API
labels: [document manager, references, replace, components, drawing views]
---
本示例演示了如何使用SOLIDWORKS文档管理器API在SOLIDWORKS文件（装配体或绘图）中替换引用（组件或绘图视图）。

* 指定父文件（例如装配体）的完整路径
* 指定要替换的文档的完整路径
* 指定新文档的完整路径

使用[SOLIDWORKS文档管理器API的ISwDMDocument::ReplaceReference](https://help.solidworks.com/2018/english/api/swdocmgrapi/solidworks.interop.swdocumentmgr~solidworks.interop.swdocumentmgr.iswdmdocument~replacereference.html)方法来替换旧的引用为新的引用。

{% code-snippet { file-name: Macro.vba } %}