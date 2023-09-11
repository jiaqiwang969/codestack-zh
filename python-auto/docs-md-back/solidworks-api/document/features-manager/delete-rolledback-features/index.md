---
layout: sw-tool
caption: Delete rolled back features
title: Macro to delete all features which are in the rolled back state in SOLIDWORKS document
description: VBA macro finds and deletes all features below the rollback bar
image: rollback-feature.svg
group: Model
---
![在功能管理器树中回滚的功能](rolled-back-features.png)

这个VBA宏删除了所有在回滚栏下的功能。

{% code-snippet { file-name: Macro.vba } %}