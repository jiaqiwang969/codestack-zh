---
layout: sw-tool
title: SOLIDWORKS macro to change layer of selected objects in drawing using SOLIDWORKS API
caption: Change Layer For Selected Objects In Drawing
description: Macro will move all selected objects in the drawing sheet to specified layer using SOLIDWORKS API
image: sw-drawing-layers.png
labels: [drawing, layer, solidworks api, utility]
group: Drawing
redirect-from:
  - /2018/03/solidworks-api-drawing-change-layer-for-selected-objects.html
---
This macro will move all selected objects in the drawing sheet to specified layer using SOLIDWORKS API.

![Drawing layers](sw-drawing-layers.png){ width=400 }

There is no common ::Layer SOLIDWORKS API property to change the layer for any entity, rather this property is added to each interface which supports it (e.g. [ISketchSegment::Layer](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isketchsegment~layer.html) property). This macro checks the type of the entity and calls corresponding SOLIDWORKS API property to change the layer.

{% code-snippet { file-name: Macro.vba } %}
