---
layout: sw-tool
title: SOLIDWORKS macro to create configuration with average dimension values
caption: Create Configuration With Average Dimension Values
description: Macro will create child configuration where all the dimension will be set to average value based on the minimum and maximum values of the tolerance
image: sw-dimension-tolerance.png
labels: [average, configuration, dimension, solidworks api, tolerance, utility]
group: Model
redirect-from:
  - /2018/03/solidworks-api-dimensions-average-dims.html
---
This macro will create child configuration where all the dimension will be set to average value based on the minimum and maximum values of the tolerance using SOLIDWORKS API.

![Dimension Tolerance/Precision group in property manager page](sw-dimension-tolerance.png){ width=400 }

{% code-snippet { file-name: Macro.vba } %}
