---
title: Handling the life cycle of SOLIDWORKS macro feature
caption: Feature Handler
description: Using SOLIDWORKS macro feature handler to manage the life cycle of the macro feature in SwEx.MacroFeature framework
toc-group-name: labs-solidworks-swex
order: 4
---
[MacroFeatureEx{TParams, THandler}类](https://docs.codestack.net/swex/macro-feature/html/T_CodeStack_SwEx_MacroFeature_MacroFeatureEx_2.htm)的宏特征重载允许定义将为每个特征创建的处理器类。这提供了一种简单的方式来跟踪宏特征的生命周期（即创建时间和删除时间）。

~~~ cs
using CodeStack.SwEx.MacroFeature;
using CodeStack.SwEx.MacroFeature.Base;
using SolidWorks.Interop.sldworks;
using System.Runtime.InteropServices;

namespace CodeStack.SwEx
{
    public class LifecycleMacroFeatureParams
    {
    }

    public class LifecycleMacroFeatureHandler : IMacroFeatureHandler
    {
        public void Init(ISldWorks app, IModelDoc2 model, IFeature feat)
        {
            //feature is created or loaded
        }
        
        public void Unload(MacroFeatureUnloadReason_e reason)
        {
            switch (reason)
            {
                case MacroFeatureUnloadReason_e.Deleted:
                    //feature is deleted
                    break;

                case MacroFeatureUnloadReason_e.ModelClosed:
                    //model is closed
                    break;
            }
        }
    }

    [ComVisible(true)]
    public class LifecycleMacroFeature : MacroFeatureEx<LifecycleMacroFeatureParams, LifecycleMacroFeatureHandler>
    {
        protected override MacroFeatureRebuildResult OnRebuild(LifecycleMacroFeatureHandler handler, LifecycleMacroFeatureParams parameters)
        {
            //TODO: access handler to extract feature specific data

            return MacroFeatureRebuildResult.FromStatus(true);
        }
    }
}

~~~



处理器类的实例将由框架创建和释放。当宏特征需要监视其所在文件的特定事件时，这种方法非常有用。