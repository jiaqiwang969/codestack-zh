---
title: Defeature Part (convert to dumb solid) using SOLIDWORKS API
caption: Defeature Part
description: Macro to convert all features in part to dumb solids (defeature part) and surfaces using SOLIDWORKS API
image: part-feature-tree-defeatured.png
labels: [defeature,parasolid]
---
该宏模拟了[零件缩减](https://help.solidworks.com/2018/english/solidworks/sldworks/c_defeature_for_parts.htm)的功能，但不直接使用它。

该宏复制所有可见的实体和曲面体，删除所有用户特征，并使用SOLIDWORKS API导入复制的实体。

**之前：**

![带有特征树的零件](part-feature-tree.png){ width=350 }

**之后：**
![缩减后的特征树零件](part-feature-tree-defeatured.png){ width=350 }

{% code-snippet { file-name: Macro.vba } %}