---
title: Create temp spherical sheet body using SOLIDWORKS modeler API
caption: Create Temp Spherical Sheet Body
description: Example demonstrates how to create temp body of a spherical sheet
image: spherical-surface.png
labels: [topology, geometry, sheet, modeler, sphere]
---
![球面片体](spherical-surface.png)

本示例演示了如何使用SOLIDWORKS API从球面创建片体。

几何体是使用[SOLIDWORKS API的IModeler::CreateSphericalSurface2](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.imodeler~createsphericalsurface2.html)方法创建的。

运行宏代码，将显示临时片体。可以旋转和选择该片体，但它不会显示在特征树中。继续执行宏以销毁该片体。

{% code-snippet { file-name: Macro.vba } %}