---
layout: sw-tool
title: 使用SOLIDWORKS API合并草图的宏
caption: 合并草图
description: 使用SOLIDWORKS API将选定的草图合并为一个单独的3D草图的VBA宏
image: merged-sketches.svg
labels: [草图,转换实体,合并]
group: 草图
---
![草图合并为3D草图](merged-3dsketch.png)

这个VBA宏使用SOLIDWORKS API将选定的草图（2D和3D）合并为一个单独的3D草图。该宏使用转换实体API将源草图的实体复制到目标草图中。

## 选项

可以通过更改宏开头的常量的值来配置宏

* *DELETE_SOURCE_SKETCHES* - 设置为True以删除原始源草图，设置为False以不删除
* *NEW_SKETCH_NAME* - 新生成的合并草图的名称，设置为空字符串以使用默认的自动生成的名称

~~~ vb
Const DELETE_SOURCE_SKETCHES As Boolean = True '删除所有源草图
Const NEW_SKETCH_NAME As String = "合并草图" '新合并草图的名称为'合并草图'
~~~

## 注意事项

* 组件装配或绘图中的草图也受支持
* 源草图的关系和尺寸不会复制到目标草图中
* 草图将合并到活动的3D草图中，或者将自动创建新的3D草图

与[按类型选择特征](/solidworks-api/document/selection/select-features-by-type/)一起使用此宏以选择要合并的所有草图。

{% code-snippet { file-name: Macro.vba } %}