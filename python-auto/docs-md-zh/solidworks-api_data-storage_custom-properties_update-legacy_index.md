---
caption: 升级遗留系统
title: 将遗留的自定义属性升级到新架构
description: VBA宏，将遗留的SOLIDWORKS自定义属性升级到SOLIDWORKS 2022的新架构中
---
该宏将遗留的自定义属性升级到[SOLIDWORKS 2022](https://help.solidworks.com/2022/english/solidworks/sldworks/c_custom_properties_architecture.htm)中的新架构。

要配置该宏，请修改宏中的常量参数。

~~~ vb
Const UPDATE_ALL_COMPS As Boolean = True
Const REBUILD_ALL_CONFIGS As Boolean = True
~~~

**UPDATE_ALL_COMPS** 设置为重新构建装配体的所有组件或仅顶层组件
**REBUILD_ALL_CONFIGS** 指定是否需要重新构建所有配置

{% code-snippet { file-name: Macro.vba } %}