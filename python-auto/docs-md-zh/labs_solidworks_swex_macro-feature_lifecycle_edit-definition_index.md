---
title: 编辑SOLIDWORKS宏特征定义
caption: 编辑定义
description: 使用SwEx.MacroFeature框架编辑SOLIDWORKS宏特征的定义
toc-group-name: 实验室-SOLIDWORKS-SwEx
order: 2
---
编辑定义允许修改现有特征的参数。当从特征管理器树中点击“编辑特征”命令时，将调用编辑定义。

![编辑特征命令](menu-edit-feature.png){ width=250 }

编辑特征的典型工作流程如下：

* 通过[IFeature::GetDefinition](https://help.solidworks.com/2016/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.ifeature~getdefinition.html)获取特征的定义。
* 通过[IMacroFeatureData::AccessSelections](https://help.solidworks.com/2016/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IMacroFeatureData~AccessSelections.html)在树中回滚特征。这将确保所有特征选择和编辑体都可用。
* 通过[GetParameters](https://docs.codestack.net/swex/macro-feature/html/M_CodeStack_SwEx_MacroFeature_MacroFeatureEx_1_GetParameters.htm)获取当前宏特征的参数。
* 创建用户界面，允许用户编辑参数。建议使用Property Manager Pages来实现特征的本机外观和体验。使用[SwEx.PMPage](/labs/solidworks/swex/pmpage/)框架简化创建属性管理器页面的方式。
* 用户界面关闭后：
    * 如果点击了“确定”，则通过[SetParameters](https://docs.codestack.net/swex/macro-feature/html/M_CodeStack_SwEx_MacroFeature_MacroFeatureEx_1_SetParameters.htm)方法设置修改后的参数，并通过[IFeature::ModifyDefinition](https://help.solidworks.com/2016/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.IFeature~ModifyDefinition.html)应用更改，此步骤还将在树中回滚宏特征。
    * 如果点击了“取消”，则通过[IMacroFeatureData::ReleaseSelectionAccess](https://help.solidworks.com/2016/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IMacroFeatureData~ReleaseSelectionAccess.html)撤消修改。

{% code-snippet { file-name: EditMacroFeatureDefinition.cs } %}

在调用[IMacroFeatureData::AccessSelections](https://help.solidworks.com/2016/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IMacroFeatureData~AccessSelections.html)、[GetParameters](https://docs.codestack.net/swex/macro-feature/html/M_CodeStack_SwEx_MacroFeature_MacroFeatureEx_1_GetParameters.htm)、[SetParameters](https://docs.codestack.net/swex/macro-feature/html/M_CodeStack_SwEx_MacroFeature_MacroFeatureEx_1_SetParameters.htm)、[IFeature::ModifyDefinition](https://help.solidworks.com/2016/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.IFeature~ModifyDefinition.html)和[IMacroFeatureData::ReleaseSelectionAccess](https://help.solidworks.com/2016/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IMacroFeatureData~ReleaseSelectionAccess.html)方法时，重要的是使用相同的指针引用[IMacroFeatureData](https://help.solidworks.com/2016/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.imacrofeaturedata.html)。