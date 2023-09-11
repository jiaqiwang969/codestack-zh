---
caption: 在所有绘图视图中选择特征
title: 在所有绘图视图中选择相应的特征
description: VBA宏，用于在所有绘图视图中选择模型中特征的相应特征
image: selected-feature.png
---
![在绘图视图中选择的特征](selected-feature.png){ width=250 }

这个VBA宏演示了如何在绘图中的每个视图中找到模型空间中输入特征的指针并选择它。

* 打开创建绘图视图的模型（例如装配或零件）
* 选择任何特征
* 运行宏。宏会停止执行
* 激活绘图
* 继续运行宏。每个视图中的所有相应特征都会被选择

## 使用GetCorresponding方法

这种方法利用了[IView::GetCorresponding](https://help.solidworks.com/2018/English/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IView~GetCorresponding.html) API方法，通过将指针从装配上下文转换为绘图视图上下文。此API仅适用于SOLIDWORKS 2018或更新版本，如果要使用另一种方法，请参考[使用SelectById2方法](#使用SelectById2方法)。

{% code-snippet { file-name: Macro.vba } %}

## 使用SelectById2方法

这种方法利用了[IModelDocExtension::SelectByID2](https://help.solidworks.com/2017/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.imodeldocextension~selectbyid2.html)，通过组合特征名称来选择特征。

{% code-snippet { file-name: MacroSelectById.vba } %}