---
title: VSTA Macro which activates feature manager tab via SOLIDWORKS API
caption: Activate Feature Manager Tab
description: Example demonstrates how to activate standard tabs (feature manager tree, property manager, configuration manager, DimXpert manager, display manager) in the feature manager view using SOLIDWORKS API
image: feature-manager-tabs.png
labels: [feature manager, tab]
---
![特征管理器选项卡](feature-manager-tabs.png)

该示例演示了如何使用SOLIDWORKS API在特征管理器视图中激活标准选项卡（特征管理器树、属性管理器、配置管理器、DimXpert管理器、显示管理器）。

* 使用*FeatMgrTab_e*枚举指定要激活的选项卡
* 运行宏（VSTA3）
* 活动选项卡将显示在消息框中
* 指定的选项卡将被激活

**ModelDocExtension.cs**
{% code-snippet { file-name: ModelDocExtension.cs } %}

**SolidWorksMacro.cs**
{% code-snippet { file-name: SolidWorksMacro.cs } %}