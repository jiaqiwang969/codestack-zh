---
layout: sw-tool
title: Copy custom properties from the drawing view to SOLIDWORKS drawing file
caption: Copy Drawing View Properties
description: VBA macro to copy specified custom properties from the selected or default drawing view into the drawing properties
image: drawing-custom-properties.png
labels: [drawing,view,custom properties]
group: Drawing
---
![SOLIDWORKS绘图中的自定义属性](drawing-custom-properties.png){ width=500 }

此宏将指定的自定义属性从绘图视图中引用的SOLIDWORKS零件或装配体复制到绘图视图本身。

可以在宏中的*PRP_NAMES*常量中指定自定义属性。使用逗号来指定要复制的多个属性。

~~~ vb
Const PRP_NAMES As String = "零件号,描述,标题"
~~~

为了在运行时选择要复制的属性，请将*PRP_NAMES*的值指定为空字符串。

~~~ vb
Const PRP_NAMES As String = ""
~~~

在这种情况下，将显示以下输入框。

![用于将属性复制到绘图的输入框](properties-input-box.png)

用户可以指定单个属性或多个属性，用逗号分隔。

如果在运行宏时选择了绘图视图，则将从该绘图视图复制属性。否则，将使用工作表属性中指定的默认属性视图（通常是绘图中的第一个视图）：

![用于自定义属性的绘图视图](properties-view.png){ width=500 }

首先，将从与绘图视图引用配置相对应的模型配置中提取自定义属性值。如果属性不存在或为空，则将提取文件特定的自定义属性。

{% code-snippet { file-name: Macro.vba } %}