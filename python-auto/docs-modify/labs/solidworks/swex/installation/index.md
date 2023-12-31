---
title: Installation and updates of SwEx.AddIn Framework for SOLIDWORKS add-ins
caption: Installation And Updates
description: Instructions on installing and updating the SwEx.AddIn framework for developing SOLIDWORKS add-ins in C# and VB.NET
image: swex-nuget-package.png
toc-group-name: labs-solidworks-swex
order: 1
---
## 安装NuGet包

在Visual Studio中的项目上下文菜单中选择“管理NuGet包...”命令

![项目上下文菜单中的“管理NuGet包...”命令](manage-nuget-packages.png){ width=250 }

在搜索框中搜索“CodeStack.SwEx”。找到后，点击所需框架的“安装”按钮。

![CodeStack.SwEx.AddIn NuGet包](swex-nuget-package.png)

这将安装所有所需的库到项目中。

## 准备项目

将SOLIDWORKS互操作库的“嵌入互操作类型”设置为“False”，如下所示。

![禁用SOLIDWORKS互操作的嵌入互操作类型选项](sw-interops-embed-inteop-types-false.png){ width=300 }

在项目属性中勾选“注册COM互操作”选项：

对于C#项目，此选项可以在“生成”选项卡中找到：

![C#项目中的注册COM互操作选项](register-for-com-interops-csharp.png){ width=300 }

对于VB.NET项目，此选项可以在“编译”选项卡中找到：

![VB.NET项目中的注册COM互操作选项](register-for-com-interops-vbnet.png){ width=300 }

## 更新

SwEx框架正在积极开发，新功能和错误修复经常发布。

NuGet提供了非常简单的升级库版本的方法。只需导航到NuGet包管理器并检查更新：

![更新NuGet包](update-nuget-packages.png)

要查看发布说明，请按照下面的链接查看相应库的版本。

* [SwEx.AddIn发布说明](https://docs.codestack.net/swex/add-in/html/version-history.htm)
* [SwEx.PMPage发布说明](https://docs.codestack.net/swex/pmpage/html/version-history.htm)
* [SwEx.MacroFeature发布说明](https://docs.codestack.net/swex/macro-feature/html/version-history.htm)

在某些情况下，更新库可能会将SOLIDWORKS互操作程序的“嵌入互操作类型”选项重置为“True”。

![更新后，SOLIDWORKS互操作选项被重置为True](embed-interop-true.png){ width=350 }

建议将其重新设置为“False”。

## 支持多个版本的SwEx框架

SwEx框架的方法签名和行为可能会在新版本中发生变化。SwEx库是强命名的，这样可以防止在同一SOLIDWORKS会话中加载多个引用不同版本框架的插件时出现兼容性冲突。