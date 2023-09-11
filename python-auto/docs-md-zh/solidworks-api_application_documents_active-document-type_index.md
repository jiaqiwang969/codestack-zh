---
title: 使用SOLIDWORKS API确定活动文档的类型
caption: 确定活动文档的类型
description: 该示例显示当前在SOLIDWORKS中活动文档的类型的消息框。
labels: [装配, 文档, 绘图, 示例, 零件, 类型]
redirect-from:
  - /2018/03/determine-type-of-active-document.html
---
该示例显示当前在SOLIDWORKS中活动文档的类型的消息框。无论文档是否已保存，此方法都适用。可以使用[IModelDoc2::GetType](https://help.solidworks.com/2018/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.IModelDoc2~GetType.html) SOLIDWORKS API方法返回类型枚举，以识别文档为SOLIDWORKS零件、装配或绘图。

{% code-snippet { file-name: Macro.vba } %}