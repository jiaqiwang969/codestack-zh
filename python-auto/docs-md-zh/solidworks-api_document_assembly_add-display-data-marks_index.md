---
layout: sw-tool
caption: 添加显示数据标记
title: 用于给主要SOLIDWORKS装配配置添加显示数据标记的宏
description: VBA宏，用于给大型装配中使用的配置添加显示数据标记，以便在大型设计审查模式下打开
image: display-data-mark.svg
group: 装配
---
这个VBA宏对于在大型设计审查模式下使用装配的用户非常有用。

默认情况下，只有活动配置会被保留以供在大型设计审查模式下使用，而装配的其他配置无法被激活：

![装配配置中没有显示标记](configuration-no-display-marks.png)

这个宏将遍历根装配的所有组件，找到所有使用的配置，并为所有配置添加显示标记数据。

![添加显示数据标记命令](add-display-data-mark.png)

这将允许在大型设计审查模式下打开所有子组件并激活使用的配置。

{% code-snippet { file-name: Macro.vba } %}