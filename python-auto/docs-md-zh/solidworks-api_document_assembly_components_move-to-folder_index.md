---
布局：sw-tool
标题：使用SOLIDWORKS API将选定的组件移动到特征文件夹
说明：将图形区域中选定的组件移动到特征管理器树中的新文件夹中的宏
图片：move-components-to-folder.png
标签：[组件，移动到文件夹]
分组：装配
---

![已添加到新文件夹的组件](new-folder.png){ width=250 }

此宏使用SOLIDWORKS API允许将选定的组件移动到特征管理器树中的新文件夹中。

可以在图形区域中选择组件（或其任何实体）。例如，只能选择组件的面或边以使宏正常工作。

{% code-snippet { file-name: Macro.vba } %}