---
layout: sw-tool
title: 删除SOLIDWORKS文件中的所有空特征文件夹的宏
caption: 删除空文件夹
description: VBA宏可删除SOLIDWORKS文件（零件或装配）中的所有空特征文件夹
image: delete-folders.svg
labels: [特征, 空, 删除, 清理]
group: 模型
---
![删除特征管理器文件夹](delete-folders.svg){ width=300 }

这个VBA宏将从活动零件或装配中删除所有空的特征文件夹。

> 仅包含空文件夹的特征文件夹也将被删除。

![从特征管理器树中删除的空文件夹](deleted-empty-folders.png)

{% code-snippet { file-name: Macro.vba } %}