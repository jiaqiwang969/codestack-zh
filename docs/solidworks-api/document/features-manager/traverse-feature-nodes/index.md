---
title: Traverse feature manager nodes using SOLIDWORKS API
caption: Traverse Feature Nodes
description: Example demonstrates how to traverse nodes in the Feature Manager Tree using SOLIDWORKS API
image: feature-manager-tree.png
labels: [traverse, feature, node]
---
![Feature Manager Tree](feature-manager-tree.png){ width=150 }

This example demonstrates how to traverse nodes in the Feature Manager Tree using SOLIDWORKS API. Nodes traversed in the exact order they are rendered in the tree and the exact text is extracted.

[ITreeControlItem](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.itreecontrolitem.html) SOLIDWORKS API interface represents the node element and allows its automation.

This macro can be useful if it is required to get the exact features hierarchy and order or get the nodes of the system features (like history, design journal etc.)

{% code-snippet { file-name: Macro.vba } %}
