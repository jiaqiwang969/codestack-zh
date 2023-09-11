---
title: 使用SOLIDWORKS PDM API递归遍历文件和文件夹
caption: 递归遍历文件夹
description: 使用SOLIDWORKS PDM API在SOLIDWORKS PDM vault中遍历并列出所选文件夹中的所有文件和文件夹的VBA示例
image: pdm-folder-structure-output.png
labels: [遍历, vault, 浏览文件夹]
---
这个VBA示例演示了如何使用SOLIDWORKS PDM API在SOLIDWORKS PDM vault中递归遍历文件和文件夹。

宏显示了内置的文件夹浏览对话框，用于选择要遍历的文件夹：

![内置的PDM文件夹浏览对话框](browse-folder.png){ width=250 }

宏递归遍历文件和子文件夹，并将文件或文件夹的名称、ID和级别输出到VBA编辑器的即时窗口。

![文件夹和文件结构输出到VBA编辑器的即时窗口](pdm-folder-structure-output.png){ width=350 }

即使树没有被[本地缓存](/solidworks-pdm-api/files/local-cache/)，这个宏也可以遍历树。 

{% code-snippet { file-name: Macro.vba } %}