---
title: 使用SOLIDWORKS API获取绘图视图中的所有可见组件
caption: 获取所有可见组件
description: 使用SOLIDWORKS API获取绘图视图中的所有可见组件（包括子装配件）的VBA宏
image: drawing-view-feature-tree.png
labels: [可见组件, 绘图视图]
---
![绘图视图特征树](drawing-view-feature-tree.png){ width=350 }

这个VBA宏使用SOLIDWORKS API从选定的绘图视图中提取所有可见组件。该宏将提取所有类型的组件（零件组件和装配组件）。

[IView::GetVisibleComponents](https://help.solidworks.com/2013/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.iview~getvisiblecomponents.html) SOLIDWORKS API方法只提取零件组件（即sldprt文件），而所有子装配组件不会被返回。此外，此函数返回的[IComponent2](https://help.solidworks.com/2017/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.IComponent2.html)接口指针是绘图上下文组件。[IComponent2::GetParent](https://help.solidworks.com/2016/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.icomponent2~getparent.html) SOLIDWORKS API方法对于所有组件都返回Nothing，这意味着无法找到父子装配。

下面的代码解决了这些限制，并返回其装配文档上下文中的所有组件。

{% code-snippet { file-name: Macro.vba } %}