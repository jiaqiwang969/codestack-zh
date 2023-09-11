---
title: Get selected sketch segments info using SOLIDWORKS API
caption: Get Selected Sketch Segments Info
description: VBA macro to get the specific information from the selected sketch segments (line, arc, parabola, spline etc.) using SOLIDWORKS API
image: selected-sketch-segments.png
labels: [sketch segment,selection]
---
![Sketch segments selected in the active sketch](selected-sketch-segments.png){ width=450 }

This VBA macro demonstrates how to extract specific sketch segment information from the selected segments using SOLIDWORKS API.

Macro will traverse all selected objects and filter sketch segments. Macro identifies the type of the segments and cast the pointer to the specific sub-type (e.g. line, spline, arc, parabola, text etc.).

Information is output to the immediate window of VBA editor.

![Sketch segments specific information is printed to Immediate window of VBA editor](printed-sketch-segments-info.png){ width=350 }

{% code-snippet { file-name: Macro.vba } %}
