---
layout: sw-tool
title: SOLIDWORKS macro to exclude selected bodies from cut-lists
caption: Exclude Selected Bodies From Cut-Lists
description: Macro excludes the solid bodies selected from the graphics area or from the feature tree from weldment or sheet metal cut-list using SOLIDWORKS API
image: excluded-cut-list-item.svg
labels: [api, cut-list, exclude, utility, vba]
group: Cut-List
---
![Exclude from cut-list](exclude-from-cut-list.png){ width=300 }

This macro allows to exclude the selected bodies from the weldment or sheet metal cut list using SOLIDWORKS API.

Bodies can be selected in the graphics view or feature tree which makes the process easier as it is not required to find the corresponding cut-list feature to exclude the body.

It is possible to use [selection filters](https://help.solidworks.com/2013/english/solidworks/sldworks/r_selection_filter_selection.htm) for bodies to simplify the picking of required ones from the graphics area.

It is also possible to select face, edge or vertex of the body to be excluded.

![Bodies to exclude from cut list selected using selection filters](filter-bodies-selection.png){ width=500 }

Watch [video demonstration](https://youtu.be/9uZCecGg25I?t=509)

{% code-snippet { file-name: Macro.vba } %}
