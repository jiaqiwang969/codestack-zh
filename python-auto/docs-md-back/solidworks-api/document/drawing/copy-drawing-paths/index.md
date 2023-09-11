---
layout: sw-tool
title: Macro to copy file paths to all drawings of an assembly components using SOLIDWORKS API
caption: Copy File Path Of All Assembly Component Drawings
description: VBA macro which copies all the referencing drawings paths of the components of the active assembly using SOLIDWORKS API
image: assembly-drawings.png
labels: [drawing,copy path,references]
group: Drawing
---
这个VBA宏使用SOLIDWORKS API找到为活动装配的所有组件创建的所有图纸，并将路径复制到剪贴板。

SOLIDWORKS提供了打开组件图纸的功能：

![在SOLIDWORKS中打开图纸的功能](open-component-drawing.png)

这个功能允许逐个查找图纸，但有时需要快速找到该装配的所有组件使用的所有图纸。这可以是自动化软件的一部分。此宏将遍历所有引用并找到所有图纸路径。完成后，将显示下面的确认消息。

![确认提取图纸操作完成](drawing-paths-copied-confirmation.png)

剪贴板的内容可以粘贴到任何文本或表格编辑器中，如记事本或Excel（使用ctrl+V快捷键或粘贴命令）。

![将图纸路径复制到Excel](drawing-paths-excel.png)

## 注意事项

* 被压制的组件将被排除在搜索范围之外
* 图纸在与输入装配相同的文件夹中搜索（包括子文件夹）
* 图纸是通过引用而不是名称进行搜索的，因此图纸可以有任何名称
* 图纸路径以换行符分隔

{% code-snippet { file-name: Macro.vba } %}