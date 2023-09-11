---
layout: sw-tool
caption: Split To Configurations
title: Macro to split SOLIDWORKS cut-list bodies into individual configurations
description: VBA macro which creates individual configurations for all cut-list bodies (or unique bodies) in the active SOLIDWORKS part document for the drawing generation purpose
image: cut-list-to-configuration.svg
group: Cut-List
---
![切割清单与配置的映射关系](cut-lists-configurations.png)

此VBA宏为活动零件文档的所有切割清单体创建单独的配置。

当准备多体切割清单零件的绘图时，此宏非常有用，因为每个唯一体都需要绘图。

宏将根据文档中的切割清单特征创建相应的配置，并设置**删除实体**特征的抑制，以便每个配置只显示单个切割清单的实体。

宏将以切割清单的名称命名配置。

宏将在SOLIDWORKS图标中显示进度条：

![操作进度](progress-bar.png)

## 配置

**KEEP_ALL_CUT_LIST_BODIES**常量用于控制宏是否隔离所有切割清单体还是仅保留单个唯一体。

~~~ vb
Const KEEP_ALL_CUT_LIST_BODIES As Boolean = True '保留所有切割清单体
~~~

如果将**KEEP_ALL_CUT_LIST_BODIES**设置为**False**，则只保留每个切割清单的第一个实体。这简化了绘图创建过程，因为只需要选择相应的引用配置来在绘图中显示实体。但是，这将导致切割清单项的数量不正确，如果插入了BOM表（始终为1）。

如果将**KEEP_ALL_CUT_LIST_BODIES**设置为**True**，则将保留每个切割清单的所有实体。在这种情况下，用户还需要通过绘图视图中的**选择实体**按钮选择要保留在绘图中的单个实体。但是，在这种情况下，BOM表将显示正确的数量。

![在绘图视图中选择实体的功能](view-select-bodies.png)

{% code-snippet { file-name: Macro.vba } %}