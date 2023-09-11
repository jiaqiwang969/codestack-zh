---
caption: Insert BOM Table
title: Macro to insert SOLIDWORKS Bill Of Materials table and attach to the anchor point
description: SOLIDWORKS VBA macro to insert Bill Of Materials (BOM) table into active or all sheets with the specified parameters and attach to the anchor point
image: bom-table-anchor.png
---
![附加到锚点的BOM表格](bom-table-anchor.png){ width=600 }

此VBA宏将物料清单（BOM）表格插入到活动的SOLIDWORKS图纸的所有或活动工作表中。工作表的第一个视图用作源视图。

BOM表格附加到BOM锚点。

修改宏中的常量以配置BOM表格选项。

~~~ vb
Const ANCHOR_TYPE As Integer = swBOMConfigurationAnchorType_e.swBOMConfigurationAnchor_TopLeft '锚点类型：swBOMConfigurationAnchor_BottomLeft，swBOMConfigurationAnchor_BottomRight，swBOMConfigurationAnchor_TopLeft，swBOMConfigurationAnchor_TopRight
Const BOM_TYPE As Integer = swBomType_e.swBomType_PartsOnly 'BOM类型：swBomType_Indented，swBomType_PartsOnly，swBomType_TopLevelOnly
Const TABLE_TEMPLATE As String = "" 'BOM模板的完整路径*.sldbomtbt，或空字符串以使用默认模板
Const INDENTED_NUMBERING_TYPE As Integer = swNumberingType_e.swNumberingType_Flat '编号类型（如果BOM_TYPE为swBomType_Indented）：swIndentedBOMNotSet，swNumberingType_Detailed，swNumberingType_Flat，swNumberingType_None
Const DETAILED_CUT_LIST As Boolean = False '详细切割清单（如果BOM_TYPE为swBomType_Indented）
Const FOLLOW_ASSEMBLY_ORDER As Boolean = True 'true以启用“按装配顺序”选项

Const ALL_SHEETS As Boolean = True 'True以处理所有工作表，False以仅处理活动工作表
~~~

{% code-snippet { file-name: Macro.vba } %}