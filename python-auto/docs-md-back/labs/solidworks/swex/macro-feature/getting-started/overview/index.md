---
title: Overview of SwEx.MacroFeature framework for SOLIDWORKS add-ins
caption: Overview
description: Generic overview of macro feature and SwEx.MacroFeature framework
toc-group-name: labs-solidworks-swex
order: 2
---
该框架提供了3个主要的宏特征抽象类，它们位于[CodeStack.SwEx.MacroFeature](https://docs.codestack.net/swex/macro-feature/html/N_CodeStack_SwEx_MacroFeature.htm)命名空间中，可以继承这些类来注册新的宏特征。

* [MacroFeatureEx](https://docs.codestack.net/swex/macro-feature/html/T_CodeStack_SwEx_MacroFeature_MacroFeatureEx.htm) - 简单的宏特征。宏特征不需要任何参数，只执行简单的操作。
* [MacroFeatureEx{TParams}](https://docs.codestack.net/swex/macro-feature/html/T_CodeStack_SwEx_MacroFeature_MacroFeatureEx_1.htm) - 参数驱动的宏特征。所有必需的输入可以在*TParams*结构（数据模型）中定义。[宏特征数据](\labs\solidworks\swex\macro-feature\data)包括：
    * 字段值（命名参数）
    * 尺寸
    * 选择集
    * 编辑实体
* [MacroFeatureEx{TParams,THandler}](https://docs.codestack.net/swex/macro-feature/html/T_CodeStack_SwEx_MacroFeature_MacroFeatureEx_2.htm) - 参数驱动的宏特征，具有为每个特征分配处理程序以跟踪生命周期的能力。

宏特征类必须是COM可见的。

建议为宏特征明确指定GUID和Prog ID。

{% code-snippet { file-name: DefiningMacroFeature.cs } %}

## 图标

可以通过[IconAttribute](https://docs.codestack.net/swex/macro-feature/html/T_CodeStack_SwEx_MacroFeature_Attributes_IconAttribute.htm)来指定自定义的宏特征图标。图标可以从资源中加载，并支持透明度。默认情况下，图标文件将创建在%ProgramData%\CodeStack\{MacroFeatureId}\Icons文件夹中，但可以通过在*iconFolderName*参数中指定来更改此位置。

## 选项

可以通过[OptionsAttribute](https://docs.codestack.net/swex/macro-feature/html/T_CodeStack_SwEx_MacroFeature_Attributes_OptionsAttribute.htm)来指定其他选项。

宏特征是一个COM对象，这意味着它需要注册才能正常运行。宏特征存储在模型中，但如果在未注册宏特征COM对象的环境中打开模型，将显示重建错误。此外，这个“悬空”的宏特征无法删除或抑制。

用户可以通过[OptionsAttribute](https://docs.codestack.net/swex/macro-feature/html/T_CodeStack_SwEx_MacroFeature_Attributes_OptionsAttribute.htm)的*provider*参数指定在“有什么问题”对话框中显示的自定义消息。指定的消息将在预定义的“插件未找到，请联系”之后显示。

{% code-snippet { file-name: UnregisteredMacroFeature.cs } %}

![未注册宏特征的重建错误消息](unregistered-macro-feature.png){ width=650 }

要插入宏特征，请使用扩展方法：[IFeatureManager::InsertComFeature](https://docs.codestack.net/swex/macro-feature/html/M_SolidWorks_Interop_sldworks_FeatureManagerEx_InsertComFeature__2.htm)。