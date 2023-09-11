---
title: 处理SOLIDWORKS宏特征的生命周期
caption: 特征处理器
description: 使用SOLIDWORKS宏特征处理器来管理SwEx.MacroFeature框架中宏特征的生命周期
toc-group-name: 实验室-SOLIDWORKS-SwEx
order: 4
---
[MacroFeatureEx{TParams, THandler}类](https://docs.codestack.net/swex/macro-feature/html/T_CodeStack_SwEx_MacroFeature_MacroFeatureEx_2.htm)的宏特征重载允许定义将为每个特征创建的处理器类。这提供了一种简单的方式来跟踪宏特征的生命周期（即创建时间和删除时间）。

{% code-snippet { file-name: FeatureHandler.cs } %}

处理器类的实例将由框架创建和释放。当宏特征需要监视其所在文件的特定事件时，这种方法非常有用。