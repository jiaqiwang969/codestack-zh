---
title: Select Named Entity (face, edge or vertex) using SOLIDWORKS API
caption: Select Named Entity
description: Select named entity (face, edge or vertex) in part, assembly (from component) or drawing (from view) using SOLIDWORKS API
image: face-name.png
labels: [face,edge,vertex,name,selection]
---
本示例演示了如何使用SOLIDWORKS API在不同的文档类型中选择命名实体（面、边或顶点）。

只能在零件文档中通过选择相应的面或边来定义命名实体：

![上下文菜单中的面属性命令](face-properties.png){ width=250 }

可以在显示的对话框中设置名称，每个零件的名称是唯一的。

![面名称对话框](face-name.png){ width=250 }

可以通过[SOLIDWORKS API方法IPartDoc::GetEntityByName](https://help.solidworks.com/2014/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IPartDoc~GetEntityByName.html)获取实体的指针。

该示例增强了功能，还允许在绘图（从所选绘图视图）或装配（从所选零件组件）中按名称选择实体。

修改*ENT_NAME*常量的值以定义不同的名称，并更改*entType*参数的值，如果需要选择边或顶点。

~~~ vb
Const ENT_NAME As String = "MyEdge1"
SelectNamedEntity swParentObject, ENT_NAME, NamedEntityType_e.Edge
~~~

{% code-snippet { file-name: Macro.vba } %}