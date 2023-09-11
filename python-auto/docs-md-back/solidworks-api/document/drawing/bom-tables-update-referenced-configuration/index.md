---
title: SOLIDWORKS macro to update referenced configuration from BOM tables
caption: Update Referenced Configuration From BOM Tables
description: Macro will update the referenced configurations for all Bill of Materials (BOM) tables on the active drawing document using SOLIDWORKS API
image: bom-configurations-property.png
labels: [bom, default view, referenced configuration, solidworks api, utility, view]
redirect-from:
  - /2018/03/update-referenced-configuration-from.html
---
该宏将使用SOLIDWORKS API在活动绘图文档上更新所有BOM表的引用配置。

![在BOM表中使用的配置列表](bom-configurations-property.png){ width=168 height=320 }

BOM表与绘图视图无关，即使视图被删除，BOM表仍将存在。
BOM表与视图的引用配置没有关联。因此，如果视图的引用配置发生更改，BOM表将不会更新。

该宏将查找所有BOM表，并根据工作表的默认视图更新它们的引用配置。

![在工作表属性中使用模型选项的自定义属性值](use-custom-prps-from-view-sheet-property.png){ width=400 height=165 }

{% code-snippet { file-name: Macro.vba } %}