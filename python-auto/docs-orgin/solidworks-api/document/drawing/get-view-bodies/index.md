---
title: Get bodies and materials from drawing view using SOLIDWORKS API
caption: Get Bodies And Materials From Drawing View
description: VBA macro to find bodies and their materials of the selected drawing view (including sheet metal flat pattern) using SOLIDWORKS API
image: sheet-metal-views.png
labels: [view bodies,flat pattern]
---
![Flat pattern drawing views](sheet-metal-views.png){ width=200 }

This VBA macro finds all bodies of the selected drawing view (including sheet metal flat pattern) and extracts their materials using SOLIDWORKS API.

[IView::Bodies](https://help.solidworks.com/2017/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.iview~bodies.html) property finds the bodies of the drawing view, however this SOLIDWORKS API property returns Nothing for the drawing view created from sheet metal flat pattern.

![Flat pattern is set in the drawing view property page](flat-pattern-view-settings.png){ width=250 }

Macro below extracts bodies and finds the materials assigned to them in both cases (for regular parts and for sheet metal patterns). The result is output to Immediate window of VBA editor.

{% code-snippet { file-name: Macro.vba } %}
