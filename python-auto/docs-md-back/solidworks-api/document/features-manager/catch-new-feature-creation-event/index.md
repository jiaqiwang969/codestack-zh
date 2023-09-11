---
title: Catch new feature creation event from SOLIDWORKS API notification
caption: Catch New Feature Creation Event
description: Example listens for feature added event of the active part document and displays the message box
labels: [event, example, feature manager, new feature, solidworks api]
redirect-from:
  - /2018/03/solidworks-api-features-manager-catch-adding-feat-event.html
---
该示例使用SOLIDWORKS API监听活动零件文档的特征添加事件。

一旦捕获到新特征创建通知，宏将向用户显示消息框。

监听器会在活动零件关闭时自动解除绑定。

*宏模块*

{% code-snippet { file-name: Macro.vba } %}

*事件监听器类*

{% code-snippet { file-name: EventListenerClass.vba } %}