---
title: Clear revision table and add new revision using SOLIDWORKS API
caption: Clear Revision Table And Add New Revision
description: Example finds the revision table and removes all revisions and then adds new row with custom data
image: sw-revision-table.png
labels: [add revision, clear revisions, drawing.revision table, example, solidworks api]
redirect-from:
  - /2018/03/solidworks-api-drawing-clear-rev-table-add-new-row.html
---

这个示例使用SOLIDWORKS API找到修订表并删除所有修订，然后添加带有自定义数据的新行。

![修订表](sw-revision-table.png){ width=640 }

[IRevisionTableAnnotation](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.irevisiontableannotation.html) 是SOLIDWORKS API接口，用于管理此类型表格的特定功能。

{% code-snippet { file-name: Macro.vba } %}