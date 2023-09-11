---
title: Macro to reconstruct spherical surface using SOLIDWORKS modeler API
caption: Reconstruct Spherical Surface
description: Example demonstrates how to create spherical surface from the selected spherical face using SOLIDWORKS API in C#
image: reconstructed-sphere.png
labels: [curve, sphere, c#]
---
![Reconstructed spherical surface from the half-sphere](reconstructed-sphere.png)

This example demonstrates how to create spherical surface (360 degress) from the selected spherical face (could be less than 360 degrees) using SOLIDWORKS API.

* Select any spherical surface and run the macro
* Reconstructed spherical surface is created as temp body and displayed in the graphics area
* Clear the selection to clear the preview

Spherical surface is created using the [IModeler::CreateSphericalSurface2](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.imodeler~createsphericalsurface2.html) SOLIDWORKS API method which is trimmed using the [ISurface::CreateTrimmedSheet4](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isurface~createtrimmedsheet4.html)

{% code-snippet { file-name: Macro.cs } %}
