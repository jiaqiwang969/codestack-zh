---
title: 使用SOLIDWORKS API通过名称在特征树中选择组件
caption: 按名称选择组件
description: 本示例演示了如何使用SOLIDWORKS API通过特征管理器树中的完整名称选择组件的最高效方法。
image: components-tree.png
labels: [选择, 组件]
---
![组件的多级树](components-tree.png){ width=200 }

本示例演示了使用SOLIDWORKS API通过组件的完整名称在装配体的任何级别上选择组件的最高效方法。

组件的名称定义为一个路径，每个级别之间用/符号分隔。组件实例ID用-符号指定（例如，FirstLevelComp-1/SecondLevelComp-2/TargetComp-1）。

组件名称可以在以下对话框中找到：

![属性对话框中的组件名称](component-name.png){ width=250 }

请参考[按名称获取组件](/solidworks-api/document/assembly/components/get-by-name)示例，了解如何在不进行选择的情况下检索到组件的指针。

{% code-snippet { file-name: Macro.vba } %}