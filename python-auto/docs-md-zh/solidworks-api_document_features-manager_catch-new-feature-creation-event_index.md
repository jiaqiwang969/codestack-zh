---
title: 从SOLIDWORKS API通知中捕获新特征创建事件
caption: 捕获新特征创建事件
description: 该示例监听活动零件文档的特征添加事件，并显示消息框。
labels: [事件, 示例, 特征管理器, 新特征, solidworks api]
redirect-from:
  - /2018/03/solidworks-api-features-manager-catch-adding-feat-event.html
---
该示例使用SOLIDWORKS API监听活动零件文档的特征添加事件。

一旦捕获到新特征创建通知，宏将向用户显示消息框。

监听器会在活动零件关闭时被解除。

*宏模块*

{% code-snippet { file-name: Macro.vba } %}

*事件监听器类*

{% code-snippet { file-name: EventListenerClass.vba } %}