---
title: How to run commands synchronously using SOLIDWORKS API
caption: Run Command Synchronously
description: Example demonstrates how to run SOLIDWORKS commands synchronously (i.e. return the execution once command closed)
image: command_open.png
labels: [sync, command, close]
---
![已打开的命令（属性管理器页面）](command_open.png){ width=250 }

[SOLIDWORKS API的ISldWorks::RunCommand](https://help.solidworks.com/2017/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isldworks~runcommand.html)方法允许运行任何命令。通常用于打开属性管理器页面。

然而，该命令是异步运行的，这意味着一旦命令开始（例如打开属性管理器页面），控制权就会返回给执行者。在某些情况下，需要在命令关闭后执行代码（例如关闭属性管理器页面）。

本示例演示了如何使用SOLIDWORKS API同步运行命令，以便在命令完成（而不是开始）后将控制权返回给执行者。

## 运行说明

* 打开/创建零件文档
* 创建任何带有矩形（或其他形状）的草图
* 选择草图
* 运行宏。结果将显示“Boss-Extrude”属性页面
* 修改选项并单击绿色勾号（确定）或叉号（取消）
* 当属性页面关闭并显示结果（确定或取消）时，宏将显示消息

### VBA宏

* 创建一个类模块，并将其命名为*CommandRunManager*。复制以下代码：

{% code-snippet { file-name: CommandRunManager.vba } %}

* 将以下代码复制到主模块（包含*main*函数的位置）
* 如果需要，修改*RunCommand*以传递任何其他命令ID。该方法在命令关闭时返回True，如果命令被取消，则返回False。

{% code-snippet { file-name: Macro.vba } %}

### C&#35;

不建议在.NET语言（C#或VB.NET）中使用DoEvents函数来模拟异步操作。最好使用[使用async和await进行异步编程](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/async/)

下面的示例演示了RunCommand的异步版本的实现，可以在不锁定UI线程的情况下等待：

**SldWorksExtension.cs**

{% code-snippet { file-name: SldWorksExtension.cs } %}

可以从任何异步方法调用该扩展。例如

{% code-snippet { file-name: Console.cs } %}