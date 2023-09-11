---
layout: sw-tool
caption: Save Bodies To Parts
title: Macro to save bodies into individual SOLIDWORKS part documents
description: VBA macro to save all bodies (or selected bodies) in the SOLIDWORKS part document to individual files
image: insert-into-new-part-pmpage.png
group: Import/Export
---
![插入到新零件属性管理器页面](insert-into-new-part-pmpage.png){ width=250 }

此宏将从活动零件文档中保存所有选定的实体（如果未选定，则保存所有实体）到单独的零件文档中。

## 配置

通过修改**CUT_LIST_PRPS_TRANSFER**常量来指定处理自定义属性传输的选项

在**OUT_DIR**中指定输出目录。如果此变量为空，则实体将保存在与源零件文档相同的目录中。

~~~ vb
Const CUT_LIST_PRPS_TRANSFER As Long = swCutListTransferOptions_e.swCutListTransferOptions_CutListProperties '将属性移动到切割列表
Const OUT_DIR As String = "D:\Parts" '将实体导出到Parts目录
~~~

## 注意事项

* 实体仍与原始零件保持链接
* 输出文件将以实体的名称命名
* 文件名中不能使用的特殊符号（例如？，*，：等）将被替换为_
* 如果输出文件夹不存在，宏将不会创建输出文件夹并且会失败

{% code-snippet { file-name: Macro.vba } %}