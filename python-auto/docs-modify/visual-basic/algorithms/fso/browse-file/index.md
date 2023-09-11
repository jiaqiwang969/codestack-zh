---
title: Show file browse for save or open in Visual Basic 6 (VBA)
caption: Browse File For Save Or Open
description: Displaying file browse dialog to select the save file path or open file path in Visual Basic 6 (VBA)
labels: [files,browse,save]
---
Excel VBA宏提供了一个辅助函数来浏览要保存的文件的名称**Application.GetSaveAsFilename**或要打开的文件的名称**Application.GetOpenAsFilename**。然而，这些函数仅在Excel VBA宏中可用，而在其他环境中不可用。

此示例演示了如何创建一个通用函数来浏览保存或打开文件。

{% code-snippet { file-name: BrowseFile.vba } %}