---
title: Recursively Traverse Files And Folders In Vault Using SOLIDWORKS PDM API
caption: Traverse Folder Recursively
description: VBA example to traverse and list all files and folders from the selected folder in SOLIDWORKS PDM vault using SOLIDWORKS PDM API
image: pdm-folder-structure-output.png
labels: [traverse,vault,browse folder]
---
这个VBA示例演示了如何使用SOLIDWORKS PDM API在SOLIDWORKS PDM vault中递归遍历文件和文件夹。

宏显示了内置的文件夹浏览对话框，用于选择要遍历的文件夹：

![内置的PDM文件夹浏览对话框](browse-folder.png){ width=250 }

宏递归遍历文件和子文件夹，并将文件或文件夹的名称、ID和级别输出到VBA编辑器的即时窗口。

![文件夹和文件结构输出到VBA编辑器的即时窗口](pdm-folder-structure-output.png){ width=350 }

即使树没有被[本地缓存](/solidworks-pdm-api/files/local-cache/)，这个宏也可以遍历树。 

{% code-snippet { file-name: Macro.vba } %}