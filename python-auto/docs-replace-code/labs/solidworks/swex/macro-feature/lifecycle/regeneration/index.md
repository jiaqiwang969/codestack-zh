---
title: Handling Regeneration method of SOLIDWORKS macro feature
caption: Regeneration
description: Handling regeneration event of SOLIDWORKS macro feature and returning bodies or errors to drive the behavior using SwEx.MacroFeature framework
toc-group-name: labs-solidworks-swex
order: 1
---
当特征正在重新构建时（无论是调用再生成还是父元素已更改），将调用此处理程序。

使用[MacroFeatureRebuildResult](https://docs.codestack.net/swex/macro-feature/html/T_CodeStack_SwEx_MacroFeature_Base_MacroFeatureRebuildResult.htm)类生成所需的输出。

特征可以生成以下输出

~~~ cs
using CodeStack.SwEx.MacroFeature;
using CodeStack.SwEx.MacroFeature.Base;
using CodeStack.SwEx.MacroFeature.Data;
using SolidWorks.Interop.sldworks;

namespace CodeStack.SwEx
{
    //returns successful regeneration without bodies
    public class RegenerationNoResultsMacroFeature : MacroFeatureEx
    {
        protected override MacroFeatureRebuildResult OnRebuild(ISldWorks app, IModelDoc2 model, IFeature feature)
        {
            return MacroFeatureRebuildResult.FromStatus(true);
        }
    }

    // returns regeneration error
    public class RegenerationRebuildErrorMacroFeature : MacroFeatureEx
    {
        protected override MacroFeatureRebuildResult OnRebuild(ISldWorks app, IModelDoc2 model, IFeature feature)
        {
            return MacroFeatureRebuildResult.FromStatus(false, "Failed to regenerate this feature");
        }
    }

    //return body without automatically assigning ids
    public class RegenerationBodyMacroFeature : MacroFeatureEx
    {
        protected override MacroFeatureRebuildResult OnRebuild(ISldWorks app, IModelDoc2 model, IFeature feature)
        {
            //use extension methods of IModeler to create a box body
            IBody2 tempBody = app.IGetModeler().CreateBox(new Point(0, 0, 0), new Vector(1, 0, 0), 0.1, 0.1, 0.1);

            return MacroFeatureRebuildResult.FromBody(tempBody, feature.GetDefinition() as IMacroFeatureData, false); 
        }
    }

    //return pattern of bodies and automatically assign entity ids
    public class RegenerationArrayOfBodiesMacroFeature : MacroFeatureEx
    {
        protected override MacroFeatureRebuildResult OnRebuild(ISldWorks app, IModelDoc2 model, IFeature feature)
        {
            IBody2[] tempBodies = null; //TODO: create temp bodies
            return MacroFeatureRebuildResult.FromBodies(tempBodies, feature.GetDefinition() as IMacroFeatureData, true);
        }
    }
}

~~~



如果特征需要创建新实体，则使用[IModeler](https://help.solidworks.com/2017/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.imodeler.html)接口。只能从再生成方法返回临时实体。

使用[IModelerExtension](https://docs.codestack.net/swex/macro-feature/html/T_SolidWorks_Interop_sldworks_ModelerEx.htm)类中提供的扩展方法。