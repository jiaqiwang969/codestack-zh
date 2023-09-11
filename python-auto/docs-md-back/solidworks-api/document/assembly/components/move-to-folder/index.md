---
layout: sw-tool
title: Move selected components to feature folder using SOLIDWORKS API
caption: Move To Folder
description: Macro move the components selected in the graphics area into a new folder in the feature manager tree
image: move-components-to-folder.png
labels: [components, move to folder]
group: Assembly
---

![已添加到新文件夹的组件](new-folder.png){ width=250 }

此宏使用SOLIDWORKS API允许将选定的组件移动到特征管理器树中的新文件夹中。

可以在图形区域中选择组件（或其任何实体）。例如，只能选择组件的面或边以使宏正常工作。

{% code-snippet { file-name: Macro.vba } %}