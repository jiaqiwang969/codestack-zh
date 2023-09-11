---
title: Select component in feature tree using its name via SOLIDWORKS API
caption: Select Component By Name
description: Example demonstrates how to select component by full name at any level of the assembly in the feature manager tree
image: components-tree.png
labels: [select, component]
---
![组件的多级树](components-tree.png){ width=200 }

本示例演示了使用SOLIDWORKS API通过组件的完整名称在装配体的任何级别上选择组件的最高效方法。

组件的名称定义为一个路径，每个级别之间用/符号分隔。组件实例ID用-符号指定（例如，FirstLevelComp-1/SecondLevelComp-2/TargetComp-1）。

组件名称可以在以下对话框中找到：

![属性对话框中的组件名称](component-name.png){ width=250 }

请参考[按名称获取组件](/solidworks-api/document/assembly/components/get-by-name)示例，了解如何在不进行选择的情况下检索到组件的指针。

{% code-snippet { file-name: Macro.vba } %}