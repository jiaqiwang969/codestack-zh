---
title: 使用SOLIDWORKS API进行扩展高级选择的宏
caption: 高级选择
description: 该宏在SOLIDWORKS装配中使用SOLIDWORKS API来扩展*高级选择*工具中可用的选择条件列表。
image: filtered-components-selection.png
labels: [选择, 固定, 包络]
---
![在特征管理器树中选择包络组件](filtered-components-selection.png){ width=250 }

该宏使用SOLIDWORKS API来扩展SOLIDWORKS装配中*高级选择*工具中的选择条件列表。

该宏允许选择以下组件（或组合）：

* Float - 未完全约束的组件（名称中带有减号（-）的组件）
* ExcludedFromBom - 从BOM中排除的组件（包括包络组件）
* Envelope - 标记为包络的组件
* NoMates - 不包含任何连接的组件

要配置该宏，请修改宏的开头处的*CRITERIA*和*TOP_LEVEL_ONLY*常量。

~~~ vb
Const CRITERIA As Integer = Criteria_e.Float + Criteria_e.NoMates
Const TOP_LEVEL_ONLY As Boolean = False
~~~

*TOP_LEVEL_ONLY*指示是否仅使用顶层组件进行过滤。将此选项设置为*True*以选择嵌套组件。

~~~ vb
Const TOP_LEVEL_ONLY As Boolean = True
~~~

*CRITERIA*是一组过滤器的组合，其中应用*Or*运算符。

例如：

~~~ vb
Const CRITERIA As Integer = Criteria_e.Float + Criteria_e.NoMates '将选择所有浮动组件或没有连接的组件
~~~

~~~ vb
Const CRITERIA As Integer = Criteria_e.Envelope '将只选择包络组件
~~~

根据需要修改宏中的过滤器。

{% code-snippet { file-name: Macro.vba } %}