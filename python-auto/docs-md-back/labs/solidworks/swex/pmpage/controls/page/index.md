---
title: Options of SOLIDWORKS Property Manager Page
caption: Page
description: Overview of options applied to the SOLIDWORKS property manager page itself
image: property-manager-page.png
toc-group-name: labs-solidworks-swex
order: 2
---
![属性管理器页面样式](property-manager-page.png)

1. 属性管理器页面的图标
2. 属性管理器页面的标题
3. 文档链接（新功能和帮助）
4. 控制按钮（确定和取消）
5. 可选的用户消息标题
6. 可选的用户消息内容

属性管理器页面的样式可以通过将 [PageOptionsAttribute](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_Attributes_PageOptionsAttribute.htm) 应用于数据模型的主类来自定义。

![带有确定和取消按钮选项的属性页面](pmpage-options.png)

{% code-snippet { file-name: Page.Options.* } %}

属性允许自定义页面的按钮和行为

## 归属

![带有自定义标题、图标和消息的属性页面](pmpage-attributes.png)

页面标题可以通过 [DisplayNameAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.displaynameattribute?view=netframework-4.7.2) 进行赋值

图标可以通过 [PageOptionsAttribute](https://docs.codestack.net/swex/pmpage/html/M_CodeStack_SwEx_PMPage_Attributes_PageOptionsAttribute__ctor_1.htm) 的重载构造函数进行设置

可以通过 [MessageAttribute](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_Attributes_MessageAttribute.htm) 设置自定义用户消息以提供额外信息

{% code-snippet { file-name: Page.Attribution.* } %}

## 帮助链接

![带有帮助和新功能链接的属性页面](pmpage-help.png)

[HelpAttribute](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_Attributes_HelpAttribute.htm) 允许为插件提供帮助资源的链接。当用户在属性管理器页面上点击相应的帮助按钮时，框架将自动打开指定的 URL：

{% code-snippet { file-name: Page.HelpLinks.* } %}