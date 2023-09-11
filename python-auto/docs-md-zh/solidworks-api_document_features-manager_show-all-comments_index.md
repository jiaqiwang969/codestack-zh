---
布局：sw-tool
标题：使用SOLIDWORKS API显示活动模型中所有评论的文本
标题：显示所有评论文本
描述：使用SOLIDWORKS API显示活动文档中评论的VBA宏
图片：comments.png
标签：[评论]
分组：模型
---
![特征管理器树中的评论](comments-features.png)

这个VBA宏从活动文档的所有评论中提取文本，并在一个单独的消息框中显示它。

{% code-snippet { file-name: Macro.vba } %}