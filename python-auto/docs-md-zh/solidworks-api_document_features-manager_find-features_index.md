---
title: 使用SOLIDWORKS API按类型和/或名称模式在树中查找特征
caption: 查找特征
description: 使用SOLIDWORKS API查找与特定特征类型名称或名称模式匹配的所有或第一个特征的VBA宏
image: feature-manager-tree.png
labels: [遍历特征,名称模式,类型名称]
---
![特征管理器树](feature-manager-tree.png){ width=250 }

此VBA宏允许使用SOLIDWORKS API在特征管理器树中查找特征。

可以通过指定类型名称和/或名称模式（支持通配符）来查找特征。将名称或类型名称设为空字符串以忽略此过滤器。

## 示例

~~~vb
Dim swFeat As SldWorks.Feature
Set swFeat = GetFirstFeature(swModel, "WeldMemberFeat") '返回第一个WeldMemberFeat类型（即结构成员）的特征
~~~

~~~vb
Dim swFeat As SldWorks.Feature
Set swFeat = GetFirstFeature(swModel, "", "Sk*") '返回名称以Sk开头的第一个特征
~~~

~~~vb
Dim vFeats As Variant
vFeats = GetAllFeatures(swModel, "WeldMemberFeat") '返回所有WeldMemberFeat类型（即结构成员）的特征
~~~

~~~vb
Dim vFeats As Variant
vFeats = GetAllFeatures(swModel, "", "Sk*")'返回名称以Sk开头的所有特征
~~~

{% code-snippet { file-name: Macro.vba } %}