---
title: Add smart dimension between two segments using SOLIDWORKS API
caption: Add Smart Dimension Between Two Segments
description: Example adds the dimension between 2 selected sketch segments
image: dimension-name.png
labels: [dimension, example, solidworks api]
redirect-from:
  - /2018/03/solidworks-api-dimensions-add-dimensions-to-sketch-segment.html
---
This example adds the dimension between 2 selected sketch segments (e.g. sketch lines) using SOLIDWORKS API. The dimension will be placed in the middle of 2 selection points.  

![Dimension with name](dimension-name.png){ width=320 height=237 }

When adding dimensions programmatically using SOLIDWORKS API it is important to disable the Input Dimension Value option otherwise the macro will be interrupted and will require user inputs.

The example below temporarily removes this option and restores the original value after the dimension inserted so user settings are not affected.  

![Option to input dimension value on creation](input-dimension-value-option.png){ width=640 height=198 }

{% code-snippet { file-name: Macro.vba } %}
