---
title: Handling the SOLIDWORKS macro feature state update in SwEx.MacroFeature framework
caption: State
description: Updating state of the macro feature on the environment change (selection, rebuild, suppress etc.) 
toc-group-name: labs-solidworks-swex
order: 3
---
每当特征的状态发生变化时，将调用此处理程序。它应该用于为宏特征提供额外的安全性。

~~~ cs
protected override swMacroFeatureSecurityOptions_e OnUpdateState(ISldWorks app, IModelDoc2 model, IFeature feature)
{
    //禁止编辑或抑制特征
    return swMacroFeatureSecurityOptions_e.swMacroFeatureSecurityCannotBeDeleted 
                | swMacroFeatureSecurityOptions_e.swMacroFeatureSecurityCannotBeSuppressed;
}
~~~