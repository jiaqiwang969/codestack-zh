---
title: Create invisible attribute using SOLIDWORKS API
caption: Create Invisible Attribute
description: Example creates an invisible attribute and attaches to the selected object (entity or component)
image: sw-attribute-features-tree.png
labels: [attribute, data, example]
redirect-from:
  - /2018/03/create-invisible-attribute.html
---
该示例创建一个不可见属性并将其附加到所选对象（实体或组件）。

可以通过在[SOLIDWORKS API方法IAttributeDef::CreateInstance5](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.iattributedef~createinstance5.html)中设置相应的标志来隐藏属性。

![属性特征插入到特征管理器树中](sw-attribute-features-tree.png){ width=272 height=320 }

一旦属性创建完成，宏将停止执行。此时，属性特征是不可见的。
当宏继续执行（按下F5或点击运行）时，该特征将变为可见。

{% code-snippet { file-name: Macro.vba } %}