---
layout: sw-tool
caption: Clear Layer
title: Remove all items from the layer in SOLIDWORKS model
description: VBA macro to remove all items (annotations, sketch segments, blocks etc) from the specified layer in SOLIDWORKS document
image: remove-layer-items.svg
group: Model
---
![SOLIDWORKS图层](solidworks-layers.png)

此VBA宏会收集并删除指定图层上的所有项目（注释、草图线段、块、草图点和填充）。图层本身不会被删除。

在**LAYER_NAME**常量中设置图层的名称。

{% code-snippet { file-name: Macro.vba } %}