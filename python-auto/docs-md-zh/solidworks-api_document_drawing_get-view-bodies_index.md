---
标题：使用SOLIDWORKS API从绘图视图获取实体和材料
说明：使用SOLIDWORKS API的VBA宏来查找所选绘图视图（包括钣金展开图）的实体和它们的材料
图片：sheet-metal-views.png
标签：[视图实体，展开图]
---

![展开图绘图视图](sheet-metal-views.png){ width=200 }

这个VBA宏使用SOLIDWORKS API来查找所选绘图视图（包括钣金展开图）的所有实体，并提取它们的材料。

[IView::Bodies](https://help.solidworks.com/2017/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.iview~bodies.html) 属性可以找到绘图视图的实体，但是对于从钣金展开图创建的绘图视图，这个SOLIDWORKS API属性会返回空值。

![在绘图视图属性页面中设置展开图](flat-pattern-view-settings.png){ width=250 }

下面的宏可以提取实体并找到它们分配的材料，无论是普通零件还是钣金展开图。结果将输出到VBA编辑器的立即窗口。

{% code-snippet { file-name: Macro.vba } %}