---
title: Handling events of SOLIDWORKS property manager page
caption: Events
description: Overview of property manager page events handling
toc-group-name: labs-solidworks-swex
order: 3
---
[PropertyManagerPageHandlerEx](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_PropertyManagerPageHandlerEx.htm)类负责向客户端提供属性管理器页面引发的事件。

处理程序的实例将由框架创建，并可以通过[PropertyManagerPageEx::Handler](https://docs.codestack.net/swex/pmpage/html/P_CodeStack_SwEx_PMPage_PropertyManagerPageEx_2_Handler.htm)属性访问。

~~~ cs
...
m_Page = new PropertyManagerPageEx<MyPMPageHandler, DataModel>(m_Data, m_App);
m_Page.Handler.Closed += r =>
{
    ...
};
...
~~~