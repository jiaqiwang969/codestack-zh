---
title: 使用 SOLIDWORKS 模型 API 重建球面的宏
caption: 重建球面
description: 本示例演示了如何使用 SOLIDWORKS API 在 C# 中从选定的球面创建球面（360度）。
image: reconstructed-sphere.png
labels: [曲线, 球面, C#]
---
![从半球面重建的球面](reconstructed-sphere.png)

本示例演示了如何使用 SOLIDWORKS API 从选定的球面（可能小于360度）创建球面（360度）。

* 选择任何球面并运行宏
* 重建的球面将作为临时实体显示在图形区域中
* 清除选择以清除预览

球面是使用 [IModeler::CreateSphericalSurface2](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.imodeler~createsphericalsurface2.html) SOLIDWORKS API 方法创建的，该方法使用 [ISurface::CreateTrimmedSheet4](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isurface~createtrimmedsheet4.html) 进行修剪。

{% code-snippet { file-name: Macro.cs } %}