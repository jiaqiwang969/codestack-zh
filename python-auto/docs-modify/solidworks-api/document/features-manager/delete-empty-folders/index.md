---
layout: sw-tool
title: Macro to delete all empty feature folders in SOLIDWORKS files
caption: Delete Empty Folders
description: VBA macro deletes all empty feature folders in the SOLIDWORKS files (part or assembly)
image: delete-folders.svg
labels: [feature, empty, delete, cleanup]
group: Model
---
![删除特征管理器文件夹](delete-folders.svg){ width=300 }

这个VBA宏将从活动零件或装配中删除所有空的特征文件夹。

> 仅包含空文件夹的特征文件夹也将被删除。

![从特征管理器树中删除的空文件夹](deleted-empty-folders.png)

{% code-snippet { file-name: Macro.vba } %}