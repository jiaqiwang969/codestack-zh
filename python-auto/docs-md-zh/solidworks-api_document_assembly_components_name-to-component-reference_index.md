---
layout: sw-tool
title: 使用SOLIDWORKS API将组件名称复制到组件引用
caption: 将组件名称复制到组件引用
description: 使用SOLIDWORKS API将活动装配中的组件名称复制到组件引用的VBA宏，具有仅筛选虚拟组件的功能
image: component-reference.png
labels: [名称,虚拟,组件引用]
group: 装配
---
![组件引用](component-reference.png){ width=350 }

此VBA宏允许使用SOLIDWORKS API将活动装配中的组件名称复制到组件引用。

通过将*VIRTUAL_ONLY*选项设置为*True*，宏可以仅处理虚拟组件。

~~~ vb
Const VIRTUAL_ONLY As Boolean = True
~~~

如果组件名称用于存储项目属性（例如零件编号），则此宏可能很有用，因为组件名称无法添加到物料清单，而组件引用可以。

![带有组件引用的物料清单](bill-of-materials.png){ width=350 }

{% code-snippet { file-name: Macro.vba } %}