---
title: Extract selection from boss-extrude feature using SOLIDWORKS API
caption: Extract Selection From Boss-Extrude Feature
description: C# VSTA macro to extract selection references (from entity, end condition and direction references) from the selected boss-extrude feature using SOLIDWORKS API
image: boss-extrude-property-page.png
labels: [selection,boss-extrude]
---
This C# VSTA macro extracts the information about the selection entities specified in the From Entity, End Condition and Direction selection boxes in the Boss-Extrude feature definition using SOLIDWORKS API.

![Boss-Extrude feature property manager page](boss-extrude-property-page.png)

Extracted data is output to the Output Window of VSTA Editor in the following format.

~~~
From Entity: Yes [swSelFACES]
End Condition (Direction 1): No
End Condition (Direction 2): No
Direction (Direction 1): Yes [swSelSKETCHSEGS]
Direction (Direction 2): No
~~~

{% code-snippet { file-name: Macro.cs } %}
