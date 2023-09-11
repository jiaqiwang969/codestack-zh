---
layout: sw-tool
title: Macro to select equal arcs in the sketch using SOLIDWORKS API
caption: Select Equal Arcs
description: VBA macro to find and select all arcs with diameter equal to the input arc using SOLIDWORKS API
image: selected-equal-arcs.png
labels: [sketch,arc,circle,equal]
group: Sketch
---
![Equal arcs selected in the sketch](selected-equal-arcs.png){ width=350 }

This VBA macro selects equal size sketch arcs to the pre-selected input sketch arc. Only arcs in the sketch of the original input arc are selected. Macro works both for active and inactive sketch.

## Options

Macro can be configured by changing the values of the constant at the beginning of the macro

~~~ vb
Const EPS As Double = 0.0000000001 'arcs radius comparison tolerance
~~~

{% code-snippet { file-name: Macro.vba } %}