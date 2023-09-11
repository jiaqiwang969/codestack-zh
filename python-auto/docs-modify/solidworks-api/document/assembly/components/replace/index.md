---
layout: sw-tool
title: Replace components preserving selection using SOLIDWORKS API
caption: Replace Components
description: Macro demonstrates how to replace selected components in the batch preserving original selections using SOLIDWORKS API
image: replace_components.png
labels: [component, replace, selection]
group: Assembly
---
![在树中替换的组件](replace_components.png){ width=350 }

该宏允许使用SOLIDWORKS API将树中选定的组件替换为指定文件夹中的组件（可选择在名称中添加附加后缀）。

在管理类似类型的项目时，该功能非常有用，其中一些文件被复制、更新和重命名，并且需要在原始装配中进行替换。

该宏使用了[SOLIDWORKS API仅选择](solidworks-api/document/selection/api-only-selection/)，可以保留原始选择的组件，避免了使用临时集合变量来满足[SOLIDWORKS API方法IAssemblyDoc::ReplaceComponents2](https://help.solidworks.com/2017/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.iassemblydoc~replacecomponents2.html)的要求，该方法要求每个组件都需要被选中以进行替换。

* 修改输入参数。通过*REPLACEMENT_DIR*设置替换零件所在的目录，并可选择使用*SUFFIX*作为文件名的后缀。

~~~ vb
Const REPLACEMENT_DIR As String = "D:\Assembly\Replacement"
Const SUFFIX As String = "_new"
~~~

* 选择组件
* 运行宏。所有组件都将被替换

{% code-snippet { file-name: Macro.vba } %}