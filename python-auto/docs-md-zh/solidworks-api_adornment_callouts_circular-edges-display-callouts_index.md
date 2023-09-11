---
layout: sw-tool
title: SOLIDWORKS宏，用于显示边缘直径的标注
caption: 显示所选圆形边缘的直径标注
description: 该宏将在3D模型中显示所有所选圆形边缘的直径值标注
image: edge-callout.svg
labels: [装饰, 标注, 直径, 边缘, 示例, 宏, SOLIDWORKS API, 单位转换]
group: 模型
redirect-from:
  - /2018/03/display-callouts-with-diameters-for-all.html
---
该宏将使用[SOLIDWORKS API方法ISelectionMgr::CreateCallout2](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.iselectionmgr~createcallout2.html)显示所有所选圆形边缘的直径值标注。

在检查模型时，同时查看多个直径值时，这将非常有用。

![在所选孔中显示的直径标注](hole-diams.png){ width=400 height=290 }

标注是SOLIDWORKS中的一种可视元素，以键值对（单行或多行）的形式显示数据。标注元素在一些标准的SOLIDWORKS工具中使用，例如[测量工具](https://help.solidworks.com/2017/english/solidworks/sldworks/t_using_the_measure_tool.htm)。通常，标注会附加到所选内容，并在取消选择对象后销毁。

运行该宏的步骤：

1. 选择圆形边缘并运行宏
2. 所有圆形边缘的直径值标注将显示在模型的单位中
3. 清除选择以删除标注

创建新的宏并将以下代码复制到宏的模块中：

![VBA编辑器中的宏模块](macro-module.png){ width=640 height=230 }

{% code-snippet { file-name: Macro.vba } %}

创建新的类模块并将其命名为*HoleDiamCalloutHandler*。

![将类模块添加到VBA宏](insert-class-module.png){ width=320 height=220 }

将以下代码复制到类模块中：

{% code-snippet { file-name: HoleDiamCalloutHandler.vba } %}