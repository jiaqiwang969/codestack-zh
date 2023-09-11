---
title: 使用SOLIDWORKS API进行缩减零件（转换为简化实体）
caption: 缩减零件
description: 使用SOLIDWORKS API将零件中的所有特征转换为简化实体（缩减零件）和曲面的宏
image: part-feature-tree-defeatured.png
labels: [缩减,Parasolid]
---
该宏模拟了[零件缩减](https://help.solidworks.com/2018/english/solidworks/sldworks/c_defeature_for_parts.htm)的功能，但不直接使用它。

该宏复制所有可见的实体和曲面体，删除所有用户特征，并使用SOLIDWORKS API导入复制的实体。

**之前：**

![带有特征树的零件](part-feature-tree.png){ width=350 }

**之后：**
![缩减后的特征树零件](part-feature-tree-defeatured.png){ width=350 }

{% code-snippet { file-name: Macro.vba } %}