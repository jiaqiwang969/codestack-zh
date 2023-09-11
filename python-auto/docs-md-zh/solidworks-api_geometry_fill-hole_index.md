---
title: 使用SOLIDWORKS API用临时几何体填充孔洞
caption: 填充孔洞
description: 这个VBA示例演示了如何使用SOLIDWORKS模型生成器和创建临时几何体来填充几何体中的孔洞。
image: filled-hole.png
labels: [填充, 模型生成器, 孔洞, 临时几何体]
---
![使用临时几何体填充的孔洞](filled-hole.png)

这个VBA示例演示了如何使用[IModeler::CreateBodyFromFaces2](https://help.solidworks.com/2017/English/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.IModeler~CreateBodyFromFaces2.html) API来填充所选特征（例如切割拉伸）中的孔洞，并生成临时几何体。

宏停止执行并显示临时几何体。继续执行以删除临时几何体。

{% code-snippet { file-name: Macro.vba } %}