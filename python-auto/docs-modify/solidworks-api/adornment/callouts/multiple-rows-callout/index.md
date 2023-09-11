---
title: Create multiple rows callout using SOLIDWORKS API
caption: Create Multiple Rows Callout
description: Example demonstrates how to create a callout with multiple rows from the selection in SOLIDWORKS API
image: sw-callout-spec.png
labels: [adornment, callout, example, note, solidworks api]
redirect-from:
  - /2018/04/solidworks-api-adornment-create-multirow-callout.html
---

本示例演示了如何使用[SOLIDWORKS API的ISelectionMgr::CreateCallout2](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.iselectionmgr~createcallout2.html)方法，在选择对象时创建具有多行的标注。

![标注元素规范](sw-callout-spec.png){ width=640 height=354 }

显示的标注的第一行是只读的，不可编辑。第二行的值可以更改。更改后的值将显示在消息框中。

*宏*

{% code-snippet { file-name: Macro.vba } %}

*CalloutHandler类*

{% code-snippet { file-name: CalloutHandler.vba } %}