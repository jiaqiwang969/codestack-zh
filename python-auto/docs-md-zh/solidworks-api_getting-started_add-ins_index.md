---
title: 如何通过API开发SOLIDWORKS自动化的插件
caption: 插件
description: 使用SOLIDWORKS API在最流行的编程语言中创建SOLIDWORKS插件的详细指南，以扩展SOLIDWORKS功能
image: add-in-load-msgbox.png
labels: [插件]
order: 3
---
SOLIDWORKS插件是SOLIDWORKS的进程内应用程序，通过使用SOLIDWORKS API实现高度定制化和最佳性能和用户体验。插件可以在启动时加载并集成到应用程序中，从而提供扩展SOLIDWORKS用户界面和功能的能力。

SOLIDWORKS插件是一个COM对象，可以使用任何兼容COM的语言进行开发，例如C++、C#、VB.NET、VB6。

为了开发插件，需要执行以下操作：

* 创建公共的COM可见类，该类实现[ISwAddIn](https://help.solidworks.com/2015/english/api/swpublishedapi/solidworks.interop.swpublished~solidworks.interop.swpublished.iswaddin.html)接口

* 使用[Regasm](https://docs.microsoft.com/en-us/dotnet/framework/tools/regasm-exe-assembly-registration-tool)将dll注册为COM服务器，用于基于.NET的插件（C#或VB.NET），使用[RegSvr32](https://en.wikipedia.org/wiki/Regsvr32)用于基于C++和VB6的插件。在注册COM对象时，需要添加dll的*codebase*。

![注册表中插件dll的COM注册信息](add-in-clsid-registry.png){ width=550 }

* 将插件的信息添加到SOLIDWORKS注册表中，以便在加载时能够识别插件。插件信息需要添加到*SOFTWARE\SolidWorks\Addins\\{AddInGuid}*和*Software\SolidWorks\AddInsStartup\\{AddInGuid}*。第一个键定义了插件的名称和描述，是必需的。第二个键是可选的，允许指定插件在SOLIDWORKS启动时是否需要加载。

![SOLIDWORKS注册表中的插件详细信息](add-in-hklm-registry.png){ width=450 }

![SOLIDWORKS注册表中的插件启动详细信息](add-in-hkcu-registry.png){ width=450 }

## 实现插件

[ISwAddIn](https://help.solidworks.com/2015/english/api/swpublishedapi/solidworks.interop.swpublished~solidworks.interop.swpublished.iswaddin.html)接口提供了两个需要实现的函数：

* [ConnectToSW](https://help.solidworks.com/2015/english/api/swpublishedapi/SolidWorks.Interop.swpublished~SolidWorks.Interop.swpublished.ISwAddin~ConnectToSW.html)。当插件与SOLIDWORKS一起加载时调用（如果指定了启动时加载选项），或者当从SOLIDWORKS的“工具”->“插件”菜单启用插件时调用。该函数传递两个参数：指向主要的[ISldWorks](https://help.solidworks.com/2015/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isldworks_members.html)接口的指针和插件的ID。

> 存储ISldWorks的指针，并在整个代码中使用它来访问所有接口。不要使用[CreateObject](https://docs.microsoft.com/en-us/dotnet/api/microsoft.visualbasic.interaction.createobject?view=netframework-4.7.2)或[Activator::CreateInstance](https://docs.microsoft.com/en-us/dotnet/api/system.activator.createinstance?view=netframework-4.7.2)方法来检索应用程序的指针，因为这种方法不能保证与当前的SOLIDWORKS实例连接，可能会启动新的后台会话。

第二个参数是插件的ID，可以在方法中使用该ID添加UI组件，例如[ISldWorks::GetCommandManager](https://help.solidworks.com/2015/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isldworks~getcommandmanager.html)、[ISldWorks::AddFileSaveAsItem2](https://help.solidworks.com/2015/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isldworks~addfilesaveasitem2.html)、[ISldWorks::ShowBubbleTooltipAt2](https://help.solidworks.com/2015/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isldworks~showbubbletooltipat2.html)

使用此方法初始化资源并创建用户界面（命令管理器、任务窗格等）。

* [DisconnectFromSW](https://help.solidworks.com/2015/english/api/swpublishedapi/SolidWorks.Interop.swpublished~SolidWorks.Interop.swpublished.ISwAddin~DisconnectFromSW.html)。当SOLIDWORKS关闭时卸载插件或从SOLIDWORKS的“工具”->“插件”菜单禁用插件时调用。使用此方法清除资源并删除所有用户界面元素（如命令管理器或任务窗格）。

> 卸载用户界面页面很重要，因为用户可以通过在插件菜单中禁用插件来卸载插件（不仅仅是关闭SOLIDWORKS应用程序），保持用户界面页面加载可能会引入崩溃或不稳定性的风险，因为页面与插件本身断开连接。

## 开发环境

SOLIDWORKS插件最流行的开发环境是[Microsoft Visual Studio](https://visualstudio.microsoft.com/)。有不同的Visual Studio版本：专业版、企业版和社区版。您可能有资格获得免费的[社区版](https://visualstudio.microsoft.com/vs/community/)。请查阅最终用户许可协议以获取更多信息。另一个免费的环境是[SharpDevelop](https://www.icsharpcode.net/)。

## 示例

以下链接提供了使用不同编程语言创建简单的“Hello World”插件的详细指南。

* [C#](csharp)
* [VB.NET](vbnet)

插件在启动时加载并显示“Hello World”消息框

![加载插件时显示的消息框](add-in-load-msgbox.png){ width=350 }

插件在SOLIDWORKS的“工具”菜单中的“插件...”对话框中可用。

![插件显示在插件对话框中](add-ins-dialog.png){ width=450 }

## 开发框架

使用免费开源的[xCAD.NET Framework](https://xcad.net/)可以大大简化在.NET（C#或VB.NET）中开发SOLIDWORKS插件的过程。该框架封装了COM类和API对象模型的复杂性，以适应.NET环境，并从语言的特性（如强类型）中受益。