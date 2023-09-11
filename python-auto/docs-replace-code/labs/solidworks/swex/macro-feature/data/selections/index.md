---
title: Managing selection of SOLIDWORKS macro feature
caption: Selections
description: Managing selections of SOLIDWORKS macro feature using the SwEx.MacroFeature framework
toc-group-name: labs-solidworks-swex
order: 2
---
~~~ cs
public class MacroFeatureParams
{
    // 任何实体的选择参数（例如面、边、特征等）
    [ParameterSelection]
    public object AnyEntity { get; set; }

    // 实体的选择参数
    [ParameterSelection]
    public IBody2 Body { get; set; }

    // 面数组的选择参数
    [ParameterSelection]
    public List<IFace2> Faces { get; set; }
~~~

参数属性可以使用直接的SOLIDWORKS类型指定，也可以使用object类型指定（如果类型未知）。还支持选择列表。

如果任何选择发生变化，将调用[OnRebuild](https://docs.codestack.net/swex/macro-feature/html/M_CodeStack_SwEx_MacroFeature_MacroFeatureEx_OnRebuild.htm)处理程序。