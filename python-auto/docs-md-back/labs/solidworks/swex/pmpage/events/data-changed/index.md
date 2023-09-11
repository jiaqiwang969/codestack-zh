---
title: SOLIDWORKS Property Manager Page data changed events handling
caption: Data Change
description: Overview of events associated with data change of SOLIDWORKS property manager page handled in SwEx.PMPage framework
toc-group-name: labs-solidworks-swex
order: 2
---
SwEx 框架提供了用于控件数据更改的事件处理程序。使用这些处理程序来更新预览或任何其他依赖于控件值的状态。

## 发布数据更改事件

[PropertyManagerPageHandlerEx::DataChanged](https://docs.codestack.net/swex/pmpage/html/E_CodeStack_SwEx_PMPage_PropertyManagerPageHandlerEx_DataChanged.htm) 事件在用户更改了更新了数据模型的控件的值后触发。请参考绑定的数据模型获取新值。

{% code-snippet { file-name: Events.DataChanged.* } %}