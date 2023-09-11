---
title: Target multiple SOLIDWORKS versions using SwEx framework
caption: Target Multiple Versions
description: How to target multiple versions of the SOLIDWORKS with the same code base using SwEx framework
image: get6-api-availability.png
toc-group-name: labs-solidworks-swex
order: 5
---
当通过NuGet包安装SwEx.Framework库时，SOLIDWORKS互操作库也会被安装。框架在其项目中引用最新的互操作库，允许用户在较新的SOLIDWORKS版本中使用最新版本的API。

尽管引用了最新的互操作库，但框架与旧版本的SOLIDWORKS兼容。**最低支持版本为SOLIDWORKS 2012**。为了实现向前兼容性，同时又能够利用较新的SOLIDWORKS版本中的新API，框架为其内部使用的API实现了回退机制。这意味着，如果框架使用的某个API在目标版本的SOLIDWORKS中不可用，将使用旧版本的API。

如果您的插件需要针对多个SOLIDWORKS版本，请使用类似的技术并实现回退API。

可以通过查看SOLIDWORKS API帮助文档（Web版和本地版）中的相应部分来了解某个方法的可用性。

![SOLIDWORKS API可用性部分](get6-api-availability.png)

使用框架提供的[ISldWorks::IsVersionNewerOrEqual](https://docs.codestack.net/swex/common/html/M_SolidWorks_Interop_sldworks_SldWorksCommonEx_IsVersionNewerOrEqual.htm)扩展方法来决定使用哪个API。例如，[ICustomPropertyManager::Get6](https://help.solidworks.com/2019/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.ICustomPropertyManager~Get6.html)方法仅在SOLIDWORKS 2018 SP0中可用，而[SOLIDWORKS 2014 SP0中可用的ICustomPropertyManager::Get5](https://help.solidworks.com/2019/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.ICustomPropertyManager~Get5.html)，以及早期版本的[SOLIDWORKS 2011 SP4中可用的ICustomPropertyManager::Get4](https://help.solidworks.com/2019/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.ICustomPropertyManager~Get4.html)。

这意味着，如果我们想在插件中提取自定义属性，并针对从SOLIDWORKS 2012开始的所有SOLIDWORKS版本，我们需要编写以下代码：

{% code-snippet { file-name: MultiTargetAddIn.Major.* } %}

> 注意。虽然可以简单地使用与所需的最低SOLIDWORKS版本相对应的最旧版本的方法，因为SOLIDWORKS支持向后兼容，但这不是推荐的做法，因为更新版本的方法可能包含关键的错误修复。

[ISldWorks::IsVersionNewerOrEqual](https://docs.codestack.net/swex/common/html/M_SolidWorks_Interop_sldworks_SldWorksCommonEx_IsVersionNewerOrEqual.htm)方法还允许检查次要版本（例如，Service Pack）。

例如，[SOLIDWORKS 2015 SP3中添加的IDimensionTolerance::GetMinValue2](https://help.solidworks.com/2019/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.idimensiontolerance~getminvalue2.html)和[IDimensionTolerance::GetMaxValue2](https://help.solidworks.com/2019/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.idimensiontolerance~getmaxvalue2.html)方法，而此方法的先前实现可在SOLIDWORKS 2006中使用。

> 注意，我们不能简单地检查当前的SOLIDWORKS版本是否为2015，因为该方法仅在SP3中有效，我们需要明确指定Service Pack。

{% code-snippet { file-name: MultiTargetAddIn.Minor.* } %}