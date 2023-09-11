---
title: SwEx.PMPage框架的概述 - 用于SOLIDWORKS API
caption: 概述
description: SwEx.PMPage框架用于在SOLIDWORKS API中构建属性管理器页面的方法的概述
image: data-model-pmpage.png
toc-group-name: labs-solidworks-swex
order: 3
---
![由数据模型驱动的属性管理器页面](data-model-pmpage.png){ width=250 }

## 数据模型

首先定义属性管理器页面需要填充的数据模型。

{% code-snippet { file-name: Overview.Simple.* } %}

使用具有公共的getter和setter的属性

## 事件处理程序

通过继承公共类[PropertyManagerPageHandlerEx](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_PropertyManagerPageHandlerEx.htm)来创建属性管理器页面的处理程序。

该类将由框架实例化，并允许处理插件中的属性管理器特定事件。

{% code-snippet { file-name: Overview.PMPageHandler.* } %}

> 类必须是COM可见的，并且必须具有公共的无参数构造函数。

## 忽略成员

如果需要从控件生成中排除数据模型中的成员，则应使用[IgnoreBindingAttribute](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_Attributes_IgnoreBindingAttribute.htm)对这些成员进行修饰。

{% code-snippet { file-name: Overview.Ignore.* } %}

## 创建实例

通过将处理程序的类型和数据模型实例传递给泛型参数来创建属性管理器页面的实例。

> 数据模型可以包含预定义（默认）值。框架将自动在相应的控件中使用这些值。

{% code-snippet { file-name: Overview.CreateInstance.* } %}

> 将数据模型实例和属性页面实例存储在类变量中。这将允许在不同的页面实例中重用数据模型。