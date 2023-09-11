---
标题：使用SOLIDWORKS API切换显示评论指示器选项
说明：使用SOLIDWORKS API和Windows API，使用VBA宏来打开和关闭特征管理器树中的“显示评论指示器”选项
图片：show-comment-indicator-command.png
标签：[winapi,comments]
---

![显示评论指示器命令](show-comment-indicator-command.png){ width=350 }

此VBA宏使用SOLIDWORKS API和Windows API的组合来切换特征管理器树中的“显示评论指示器”选项，该选项目前在SOLIDWORKS API中不可用。

{% code-snippet { file-name: Macro.vba } %}