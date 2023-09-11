---
title: Traverse feature manager nodes using SOLIDWORKS API
caption: Traverse Feature Nodes
description: Example demonstrates how to traverse nodes in the Feature Manager Tree using SOLIDWORKS API
image: feature-manager-tree.png
labels: [traverse, feature, node]
---
![特征管理器树](feature-manager-tree.png){ width=150 }

这个示例演示了如何使用SOLIDWORKS API遍历特征管理器树中的节点。节点按照它们在树中呈现的顺序进行遍历，并提取出确切的文本。

[ITreeControlItem](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.itreecontrolitem.html) SOLIDWORKS API接口表示节点元素，并允许自动化操作。

如果需要获取确切的特征层次结构和顺序，或者获取系统特征的节点（如历史记录、设计日志等），这个宏可能会很有用。

{% code-snippet { file-name: Macro.vba } %}