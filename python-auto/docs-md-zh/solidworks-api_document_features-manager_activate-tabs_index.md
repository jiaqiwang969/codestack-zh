---
title: 通过SOLIDWORKS API激活特征管理器选项卡的VSTA宏
caption: 激活特征管理器选项卡
description: 该示例演示了如何使用SOLIDWORKS API在特征管理器视图中激活标准选项卡（特征管理器树、属性管理器、配置管理器、DimXpert管理器、显示管理器）
image: feature-manager-tabs.png
labels: [特征管理器, 选项卡]
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