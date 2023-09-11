---
title: Create temp toroidal sheet body using SOLIDWORKS modeler API
caption: Create Temp Toroidal Sheet Body
description: Example demonstrates how to create temp body of a toroidal sheet
image: toroidal-surface.png
labels: [topology, geometry, sheet, modeler, cylinder]
---
![Toroidal sheet body](toroidal-surface.png)

This example demonstrates how to create a sheet body from the toroidal surface using SOLIDWORKS API.

Geometry is created using the [IModeler::CreateToroidalSurface](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.imodeler~createtoroidalsurface.html) SOLIDWORKS API method.

Run the macro and temp body is displayed. Body can be rotated and selected but it is not presented in the feature tree. Continue the macro execution to destroy the body.

{% code-snippet { file-name: Macro.vba } %}
