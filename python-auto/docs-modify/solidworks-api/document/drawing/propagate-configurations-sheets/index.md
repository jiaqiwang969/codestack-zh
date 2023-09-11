---
caption: Propagate Configurations To Sheets
title: Macro propagates configurations of the referenced document to sheets in the SOLIDWORKS drawings
description: VBA macro copies the input sheet and sets the referenced configuration sof the referenced document
image: sheets.png
---

![具有多个工作表的图纸](sheets.png){ width=800 }

此VBA宏将复制活动工作表并将引用配置传播到每个副本。

宏将自动在每个新工作表上设置引用配置，并根据配置名称重命名工作表。

结果图纸将包含多体零件或装配体的所有配置的工作表。

## 配置

可以通过更改宏的常量值来配置宏

~~~ vb
Const TOP_LEVEL_CONFIGS_ONLY As Boolean = False 'True表示仅处理顶层配置，False表示处理子配置
Const USE_CORRESPONDING_FLAT_PATTERN_CONF As Boolean = True 'True表示查找平面图视图的相应SM-FLAT-PATTERN配置，False表示使用配置As Is
Const GENERATE_MISSING_FLAT_PATTERN_CONF As Boolean = True 'True表示如果不存在，则自动创建新的SM-FLAT-PATTERN配置，False表示使用配置As Is
~~~

## 注意事项

* 宏将跳过处理系统配置（例如焊接件的焊接和加工配置，钣金平面图配置和速度包配置）
* 宏不会为在工作表的默认（第一个）视图中使用的相同配置创建另一个工作表（模板工作表）

### 钣金平面图

当从用户界面创建平面图的绘图视图时，会自动添加新的特殊配置（SM-FLAT-PATTERN）。此配置将设置为引用配置。通过SOLIDWORKS API分配引用视图时，可以强制将标准配置分配给平面图视图，这将导致显示不正确。用户需要手动重新检查**平面图**切换或重置引用配置。宏的**USE_CORRESPONDING_FLAT_PATTERN_CONF**选项允许查找平面图配置（如果存在），并将其用于平面图视图。如果找不到，可以通过设置宏的**GENERATE_MISSING_FLAT_PATTERN_CONF**选项来自动创建平面图视图。

{% code-snippet { file-name: Macro.vba } %}