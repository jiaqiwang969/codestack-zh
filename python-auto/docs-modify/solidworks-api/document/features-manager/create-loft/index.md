---
caption: Create Loft Feature
title: Create loft feature through selected sketches or curves feature using SOLIDWORKS API
description: VBA macro to create solid loft feature from selected sketch or curve features using SOLIDWORKS API
image: loft-feature-through-curves.png
---

![通过曲线创建阁楼特征](loft-feature-through-curves.png){ width=400 }

这个VBA宏演示了如何利用[IFeatureManager::InsertProtrusionBlend2](https://help.solidworks.com/2018/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.IFeatureManager~InsertProtrusionBlend2.html) API从在特征管理器树中选择的草图或曲线特征创建阁楼特征。

{% code-snippet { file-name: Macro.vba } %}