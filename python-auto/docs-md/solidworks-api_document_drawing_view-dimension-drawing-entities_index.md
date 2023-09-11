---
title: Dimension visible drawing entities from view using SOLIDWORKS API
caption: Dimension Visible Entities
description: Find and dimension the longest visible entity in the drawing view using SOLIDWORKS API
image: longest-edge-dimension.png
labels: [drawing,dimension,visible entities]
---
![Longest edge dimensioned in the drawing view](longest-edge-dimension.png){ width=250 }

This example demonstrates how to add a linear dimension to the longest edge in the selected drawing view using SOLIDWORKS API.

This macro is traversing all visible entities in the drawing view, calculates the length of the edge and finds the longest one. Macro will only work if the longest edge can be dimensioned (i.e. it is either linear or circular edge).

The entities returned from [IView::GetVisibleEntities](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.iview~getvisibleentities.html) are already in the drawing view context and they could be selected directly via [IEntity::Select4](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.ientity~select4.html) SOLIDWORKS API method and it is not required to call the [IView::SelectEntity](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.iview~selectentity.html) function.

Location of the dimension is calculated by offsetting the middle point of the dimensioned edge in the normal curve direction (cross product of the tangent direction and the sheet Z axis) by 20% of the edge length. Unlike [drawing in sheet context](/solidworks-api/document/drawing/sheet-context-sketch/), drawing sheet scale is not required to be multiplied to the view transformation matrix when positioning the dimensions.

{% code-snippet { file-name: Macro.vba } %}
