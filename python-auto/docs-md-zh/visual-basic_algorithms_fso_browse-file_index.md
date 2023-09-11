---
title: 在Visual Basic 6 (VBA)中显示文件浏览器以保存或打开文件
caption: 浏览文件以保存或打开
description: 在Visual Basic 6 (VBA)中显示文件浏览对话框以选择保存文件路径或打开文件路径
labels: [文件,浏览,保存]
---
Excel VBA宏提供了一个辅助函数来浏览要保存的文件的名称**Application.GetSaveAsFilename**或要打开的文件的名称**Application.GetOpenAsFilename**。然而，这些函数仅在Excel VBA宏中可用，而在其他环境中不可用。

此示例演示了如何创建一个通用函数来浏览保存或打开文件。

{% code-snippet { file-name: BrowseFile.vba } %}