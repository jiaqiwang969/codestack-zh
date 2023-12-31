---
title: Determine if selected face is hole or boss using SOLIDWORKS API
caption: Determine If The Selected Face Is Hole Or Boss
description: Example demonstrates how to identify if the selected cylindrical face in SOLIDWORKS part or assembly is internal (i.e. hole) or external (i.e. boss) using SOLIDWORKS API based on the normals of the face.
image: boss-hole.png
labels: [geometry, hole, boss]
---
![体内的孔和凸台](boss-hole.png){ width=250 }

该示例演示了如何使用SOLIDWORKS API来确定所选的圆柱面是内部（即孔）还是外部（即凸台）。

选择圆柱面并运行宏。将显示带有所选面类型的消息框。该宏适用于任何面（面不需要具有平面相邻面）。

### 算法

该宏根据面的法线方向来确定面是孔还是凸台。孔的法线始终指向圆柱轴，而凸台的法线始终指向圆柱轴外部。

宏在面上找到一个随机点（在本示例中，这是面的U和V参数之间的中点），并计算该点处的法线。然后计算该点与圆柱体原点之间的向量。如果该向量与法线之间的角度小于90度（PI / 2），则法线指向圆柱轴，这意味着该面是孔；否则（如果角度大于90度（PI / 2）），该面是外部的（凸台）。

请参见下图：

![孔和凸台的法线](inner-face-outer-face.png){ width=400 }

{% code-snippet { file-name: Macro.* } %}