---
title: 使用SOLIDWORKS API选择与属性相关联的组件
caption: 在选择中选择与属性相关联的组件
description: 该示例通过[SOLIDWORKS API](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.dassemblydocevents_newselectionnotifyeventhandler.html)通知，将其附加到活动装配的选择事件上。
labels: [属性, 组件, 数据, 示例, 选择, solidworks api]
redirect-from:
  - /2018/03/select-components-associated-with.html
---
该示例通过[SOLIDWORKS API](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.dassemblydocevents_newselectionnotifyeventhandler.html)通知，将其附加到活动装配的选择事件上。

如果选择了属性并且有与该属性相关联的组件，则该组件将在树中被选中。

一旦活动装配关闭，宏将停止运行。

*宏模块*

{% code-snippet { file-name: Macro.vba } %}

*事件监听器类*

{% code-snippet { file-name: EventsListenerClass.vba } %}