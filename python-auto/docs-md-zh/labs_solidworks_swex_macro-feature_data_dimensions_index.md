---
title: 使用SwEx.MacroFeature框架管理SOLIDWORKS宏特征中的尺寸
caption: 尺寸
description: 使用SwEx.MacroFeature框架将尺寸（线性和径向）添加到SOLIDWORKS宏特征中
toc-group-name: 实验室-SOLIDWORKS-SwEx
order: 4
---
尺寸是宏特征的额外输入源。可以通过以下方式定义尺寸：

{% code-snippet { file-name: DimensionsParameters.cs } %}

在重建后需要重新排列尺寸，可以通过重写[OnSetDimensions](https://docs.codestack.net/swex/macro-feature/html/M_CodeStack_SwEx_MacroFeature_MacroFeatureEx_1_OnSetDimensions.htm)方法来实现。使用[DimensionData::SetOrientation](https://docs.codestack.net/swex/macro-feature/html/M_CodeStack_SwEx_MacroFeature_Data_DimensionDataExtension_SetOrientation.htm)辅助方法来对齐尺寸。

{% code-snippet { file-name: SetDimensions.cs } %}

*Origin*是尺寸的起点。

对于线性尺寸，*orientation*表示沿尺寸方向的向量（即测量实体的方向）。
对于径向尺寸，*orientation*表示尺寸的法线（即尺寸的旋转向量）。

![尺寸的方向](dimensions-orientation.png){ width=350 }

### 从重建中传递数据

在某些情况下，可能需要从[OnRebuild](https://docs.codestack.net/swex/macro-feature/html/M_CodeStack_SwEx_MacroFeature_MacroFeatureEx_1_OnRebuild.htm)方法中传递数据以在[OnSetDimensions](https://docs.codestack.net/swex/macro-feature/html/M_CodeStack_SwEx_MacroFeature_MacroFeatureEx_1_OnSetDimensions.htm)中使用。例如，当需要使用几何形状来计算尺寸位置时。

可以通过创建自定义重建结果并从重建函数中返回来实现这一点。

{% code-snippet { file-name: DimensionRegenerationData.cs } %}