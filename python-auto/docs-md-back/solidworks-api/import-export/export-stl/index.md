---
layout: sw-tool
title: Export part or selected component to STL using SOLIDWORKS API
caption: Export Part Or Component To STL
description: Macro exports selected assembly component or part to stl format without the need of activating the document. Macro can optionally apply transformation to the exported STL to reorient the output
image: stl-component.svg
labels: [component, export, stl]
group: Import/Export
redirect-from:
  - /solidworks-api/import-export/export-component-stl/
---
![导出为STL的选定组件](component-stl.png){ width=250 }

这个C# VSTA宏使用SOLIDWORKS API将活动零件或选定的装配组件导出为STL格式。该宏也适用于加载轻量级组件。

该宏不使用默认的导出器，并克服了模型需要在自己的窗口中加载时的限制，即不使用[IModelDocExtension::SaveAs](https://help.solidworks.com/2017/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.imodeldocextension~saveas.html) SOLIDWORKS API函数。该宏将从模型的三角剖分三角形创建stl。

该宏可以选择性地应用变换来旋转或移动STL文件。不需要为此创建坐标系。

有关STL规范的更多信息，请参阅[此链接](https://en.wikipedia.org/wiki/STL_(file_format))。

## 配置方向

为了配置输出文件的方向，需要在宏的开头更改*m_Transform*中定义的4x4方向矩阵的值。

使用[获取坐标系变换](/solidworks-api/geometry/transformation/get-coordinate-system-transform/)宏从任何选定的坐标系中检索变换。

例如，要设置绕X轴顺时针方向旋转90度，需要将*m_Transform*数组的值更改为以下值：

~~~ cs
private double[] m_Transform = new double[]
{
    1,-0,0,0,
    0,-1,0,1,
    0,0,0,0,
    1,0,0,0
};
~~~

## 运行说明

* 打开零件

或者

* 打开装配体（可以以轻量级方式打开）
* 选择零件组件
* 浏览输出STL文件的位置
* 文件被导出

{% code-snippet { file-name: Macro.cs } %}
