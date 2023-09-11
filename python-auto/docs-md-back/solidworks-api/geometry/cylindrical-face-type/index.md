---
title: Get type of cylindrical face using SOLIDWORKS API
caption: Get Type Of Cylindrical Face
description: Macro identifies the type of the selected simple cylindrical face (through all hole, blind hole or external hole) using SOLIDWORKS API based on the loops type
image: cylindrical-faces-types.png
labels: [geometry, face, hole, outer, inner]
---

![圆柱面类型](cylindrical-faces-types.png){ width=250 }

该宏通过SOLIDWORKS API基于环类型，识别所选简单圆柱面的类型（全孔、盲孔或外孔）。

该宏仅适用于相邻面为平面面且圆柱体的上下边界为封闭圆边的圆柱面。

### 算法

宏遍历上下边界边的共边环。如果存在至少一个内部环，表示所选面为孔洞；否则为外部凸台。如果两个边界环都是内部环，则表示孔洞为全孔；如果一个边界环为外部环，另一个为内部环，则表示所选面为盲孔（即非全孔）。

{% code-snippet { file-name: Macro.vba } %}