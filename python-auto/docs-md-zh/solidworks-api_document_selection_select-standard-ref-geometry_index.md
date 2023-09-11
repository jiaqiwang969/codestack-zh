---
layout: sw-tool
title: 使用SOLIDWORKS API按类型选择标准参考几何体（例如前平面或原点）
caption: 按类型选择标准平面或原点
description: 本示例演示了如何使用SOLIDWORKS API按类型选择标准平面（顶部、前部或右侧）和原点，以便无论平面名称如何，选择都是一致的，因为不建议按名称选择标准平面，因为名称不一致，可能会在模板中更改（例如不同的本地化或标准）。
image: plane.svg
labels: [选择, 平面, 原点]
group: 模型
redirect-from:
  - /solidworks-api/document/selection/select-standard-plane/
---
![在图形视图中选择了右平面](selected-right-plane.png){ width=400 }

本示例演示了如何使用SOLIDWORKS API按类型选择标准平面（顶部、前部或右侧）或原点，通过指定其类型来实现选择的一致性，因为不建议按名称选择标准平面，因为名称不一致，可能会在模板中更改（例如不同的本地化或标准）。

此宏选择根文档的主平面或原点。要选择装配体中特定组件的主平面或原点，请将鼠标悬停在任何组件实体上（无需选择），然后运行宏。

此宏基于默认的SOLIDWORKS平面始终以相同的顺序排序的事实，即前部、顶部和右侧平面是模型中的第一个平面，在原点特征之前放置，并且无法重新排序或删除。

{% youtube id: zUqHCUNxJoA %}

## 配置

### 目标平面或原点

要配置宏，请将要选择的平面类型设置为**REF_GEOM**变量。支持的值：**Right**、**Top**、**Front**、**Origin**

~~~ vb
Dim REF_GEOM As swRefGeom_e
~~~

~~~ vb jagged
#Else
    REF_GEOM = swRefGeom_e.Right 
#End If
~~~

### 滚动到选择

此宏允许通过设置**SCROLL**常量来指定是否应将平面滚动到视图中

~~~ vb
Const SCROLL As Boolean = False' 滚动平面到视图中
~~~

> 注意，此宏将忽略**特征管理器 -> 将选定项滚动到视图中**选项，并根据上述选项滚动，保留SOLIDWORKS中的设置。

### 追加选择

如果按下**ctrl**键，宏将追加选择，除非将**APPEND_SEL**常量设置为true。在这种情况下，选择将始终追加。当使用宏按钮的快捷方式时，这很有用，因为**ctrl**将与快捷方式冲突。

~~~ vb
Const APPEND_SEL As Boolean = True
~~~

## CAD+

此宏与[Toolbar+](https://cadplus.xarial.com/toolbar/)和[Batch+](https://cadplus.xarial.com/batch/)工具兼容，因此可以将按钮添加到工具栏并分配快捷方式以便更轻松地访问或批处理运行。

![工具栏中的按钮](toolbar.png)

要启用[宏参数](https://cadplus.xarial.com/toolbar/configuration/arguments/)，请将**ARGS**常量设置为true

~~~ vb
#Const ARGS = True
~~~

在这种情况下，不需要复制宏来设置单独的[目标平面或原点](#target-plane-or-origin)。而是使用相应目标实体的**FRONT**、**TOP**、**RIGHT**、**ORIGIN**参数。

您可以下载每个按钮的图标：[前平面](front.svg)、[顶部平面](top.svg)、[右平面](right.svg)、[原点](origin.svg)，或使用您自己的图标。

{% code-snippet { file-name: Macro.vba } %}