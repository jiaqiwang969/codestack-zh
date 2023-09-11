---
title: Convert arc to circle by merging end points using SOLIDWORKS API
caption: Convert Arc To Circle
description: VBA macro to convert sketch arc to a sketch circle by adding the merge relation between start and end points using SOLIDWORKS API
image: sketch-arc.png
labels: [sketch,arc,circle,merge,relation]
---
![Sketch arc](sketch-arc.png){ width=350 }

This VBA macro example demonstrates how to apply the merge sketch relation between start and end points of the selected sketch arc to convert it to sketch circle. This is the analogue of dragging the point manually until it is merged or adding the merge sketch relation in relation manager.

{% code-snippet { file-name: Macro.vba } %}