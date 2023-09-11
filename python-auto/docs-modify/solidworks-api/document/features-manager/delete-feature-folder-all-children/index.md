---
layout: sw-tool
title: SOLIDWORKS Macro to delete feature folder with all children features
caption: Delete Feature Folder With All Children Features
description: Macro allows to delete all of the features in the selected folder in one click using SOLIDWORKS API
image: deleted-folder-features.svg
labels: [delete folder, feature manager, folder, solidworks api, utility]
group: Model
redirect-from:
  - /2018/04/solidworks-api-feature-manager-delete-feature-folder-with-all-children.html
---

在SOLIDWORKS特征树中删除顶层文件夹时，所有子特征都不会被删除，因此需要逐个选择它们以删除文件夹内容。

由于特征之间的关系，这并不总是能够一次完成：

![手动删除文件夹特征](delete-features-manually.gif){ width=400 }

下面的宏使用SOLIDWORKS API，允许一键删除所选文件夹中的所有特征。支持嵌套文件夹。

![删除包含所有子特征的文件夹](delete-folder-with-features.png){ width=400 }

宏可以选择是否显示确认对话框，其中列出将要被删除的特征列表。

观看[视频演示](https://youtu.be/9uZCecGg25I?t=396)

{% code-snippet { file-name: Macro.vba } %}