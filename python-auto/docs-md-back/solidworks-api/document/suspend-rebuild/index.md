---
layout: sw-tool
title: Macro to suspend rebuild operation in SOLIDWORKS model using API
caption: Suspend Rebuild Operation
description: This macro allows to suspend rebuild operation for parts, assemblies and drawings to enhance the performance using SOLIDWORKS API
image: suspended-rebuild.svg
labels: [api, rebuild, utility, suspend, performance]
group: Performance
---
该宏使用SOLIDWORKS API来暂停零件、装配体和图纸的重建操作，以提高性能。

![更改尺寸时暂停重建的演示](rebuild-suspended.gif)

当宏启动时，会显示一个表单。在表单打开期间，所有重建操作（重新生成）都将被暂停。
例如，直到点击**退出暂停重建模式**按钮之前，尺寸更改或配合关系都不会解决。

[下载宏](FreezeRebuild.swp)

**主模块**

{% code-snippet { file-name: Macro.vba } %}

**用户表单**

{% code-snippet { file-name: FreezeRebuildForm.vba } %}