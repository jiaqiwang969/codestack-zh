---
layout: sw-tool
title: Show the text of all comments in the active model using SOLIDWORKS API
caption: Show All Comments Text
description: VBA macro to show text from comments in the active document using SOLIDWORKS API
image: comments.png
labels: [comment]
group: Model
---
![特征管理器树中的评论](comments-features.png)

这个VBA宏从活动文档的所有评论中提取文本，并在一个单独的消息框中显示它。

{% code-snippet { file-name: Macro.vba } %}