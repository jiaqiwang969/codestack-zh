---
title: Storing parameters in SOLIDWORKS macro feature
caption: Parameters
description: Storing the parameters structure in SOLIDWORKS macro feature using SwEx.MacroFeature framework
toc-group-name: labs-solidworks-swex
order: 1
---
参数是宏特征所需的任何附加元数据。目前仅支持基本类型的参数（例如字符串、布尔值、双精度浮点数、整数等）。

~~~ cs
public class MacroFeatureParams
{
    public string Parameter1 { get; set; }
    public int Parameter2 { get; set; }
}

//此宏特征有两个参数（Parameter1和Parameter2）
[ComVisible(true)]
public class MyMacroFeature : MacroFeatureEx<MacroFeatureParams>
{
}
~~~