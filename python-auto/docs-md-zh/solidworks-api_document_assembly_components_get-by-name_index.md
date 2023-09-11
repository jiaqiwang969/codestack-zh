---
title: 使用SOLIDWORKS API通过名称获取组件的指针
caption: 通过名称获取组件
description: 该示例演示了如何从组件的完整名称层次结构中检索组件在装配体的任何级别上的指针
image: components-tree.png
labels: [选择, 组件]
---
![组件的多级树形结构](components-tree.png){ width=200 }

该示例演示了如何从组件的完整名称层次结构中检索到[SOLIDWORKS API的IComponent2](https://help.solidworks.com/2017/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.icomponent2.html)方法的指针，该方法可以在装配体的任何级别上使用。

组件的名称被定义为一个路径，每个级别之间用/符号分隔。组件实例ID用-符号指定（例如：FirstLevelComp-1/SecondLevelComp-2/TargetComp-1）。

在SOLIDWORKS用户界面中，可以在以下对话框中找到组件名称：

![属性对话框中的组件名称](component-name.png){ width=250 }

有关通过名称选择组件的另一种方法，请参阅[通过名称选择组件](/solidworks-api/document/selection/select-component-by-name)示例。

{% code-snippet { file-name: Macro.vba } %}