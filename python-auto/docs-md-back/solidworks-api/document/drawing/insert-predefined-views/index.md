---
caption: Insert Predefined Views
title: Macro to insert model into the predefined views of the SOLIDWORKS drawing template
description: VBA macro allows to insert SOLIDWORKS model into all or selected predefined views of the active drawing document
image: predefined-views.png
---
![SOLIDWORKS预定义视图](predefined-views.png){ width = 400 }

此VBA宏允许将SOLIDWORKS零件或装配体插入活动绘图或绘图模板的预定义视图中

选择要插入模型的预定义绘图视图。如果未选择任何视图，则将填充所有预定义视图。

宏将显示文件浏览对话框以选择要插入的模型。

{% code-snippet { file-name: Macro.vba } %}