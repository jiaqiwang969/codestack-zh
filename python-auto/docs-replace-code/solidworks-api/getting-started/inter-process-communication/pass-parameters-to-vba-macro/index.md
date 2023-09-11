---
title: Pass Parameters To SOLIDWORKS VBA Macro
caption: Pass Parameters To VBA Macro
description: Workarounds for passing parameters to SOLIDWORKS VBA macro from external applications
labels: [arguments,parameters,interoperability]
---
SOLIDWORKS VBA宏不接受自定义参数作为输入，因此无法将用户参数传递给[ISldWorks::RunMacro2](https://help.solidworks.com/2012/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isldworks~runmacro2.html)方法。这个限制可能是使用API自动化SOLIDWORKS的主要障碍。

在某些情况下，这可能是一个方便的功能，例如在更大的自动化过程中，多个宏需要共享相同的参数（例如输出位置、时间戳等）。或者是从服务器应用程序或通过调度软件启动的过程，生成需要传递给宏的输入。

本节介绍了解决此限制的替代方法的实现，并提供了示例。

* [通过剪贴板](通过剪贴板)
* [通过SWB宏](通过SWB宏)