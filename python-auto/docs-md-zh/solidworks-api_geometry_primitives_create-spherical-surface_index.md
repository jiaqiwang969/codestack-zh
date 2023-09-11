---
title: 使用SOLIDWORKS模型API创建临时球面片体
caption: 创建临时球面片体
description: 本示例演示了如何使用SOLIDWORKS API从球面创建片体。
image: spherical-surface.png
labels: [拓扑结构, 几何, 片体, 模型, 球体]
---
![球面片体](spherical-surface.png)

本示例演示了如何使用SOLIDWORKS API从球面创建片体。

几何体是使用[SOLIDWORKS API的IModeler::CreateSphericalSurface2](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.imodeler~createsphericalsurface2.html)方法创建的。

运行宏代码，将显示临时片体。可以旋转和选择该片体，但它不会显示在特征树中。继续执行宏以销毁该片体。

{% code-snippet { file-name: Macro.vba } %}