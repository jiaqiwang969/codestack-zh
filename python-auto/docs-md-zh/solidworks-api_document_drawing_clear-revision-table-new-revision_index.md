---
标题：清除修订表并使用SOLIDWORKS API添加新的修订
说明：示例找到修订表并删除所有修订，然后添加带有自定义数据的新行
图片：sw-revision-table.png
标签：[添加修订，清除修订，图纸.修订表，示例，solidworks api]
重定向自：
  - /2018/03/solidworks-api-drawing-clear-rev-table-add-new-row.html
---

这个示例使用SOLIDWORKS API找到修订表并删除所有修订，然后添加带有自定义数据的新行。

![修订表](sw-revision-table.png){ width=640 }

[IRevisionTableAnnotation](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.irevisiontableannotation.html) 是SOLIDWORKS API接口，用于管理此类型表格的特定功能。

{% code-snippet { file-name: Macro.vba } %}