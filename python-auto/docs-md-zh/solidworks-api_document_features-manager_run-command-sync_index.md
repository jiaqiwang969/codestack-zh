---
title: 如何使用SOLIDWORKS API同步运行命令
caption: 同步运行命令
description: 本示例演示了如何使用SOLIDWORKS API同步运行命令（即在命令关闭后返回执行）。
image: command_open.png
labels: [同步, 命令, 关闭]
---
![已打开的命令（属性管理器页面）](command_open.png){ width=250 }

[SOLIDWORKS API的ISldWorks::RunCommand](https://help.solidworks.com/2017/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isldworks~runcommand.html)方法允许运行任何命令。通常用于打开属性管理器页面。

然而，该命令是异步运行的，这意味着一旦命令开始（例如属性管理器页面已打开），控制权就会返回给执行者。在某些情况下，需要在该命令关闭后执行代码（例如属性管理器页面已关闭）。

本示例演示了如何使用SOLIDWORKS API同步运行命令，以便在命令完成（而不是开始）后将控制权返回给执行者。

## 运行说明

* 打开/创建零件文档
* 创建任何形状的草图，如矩形
* 选择草图
* 运行宏。结果将显示“Boss-Extrude”属性页面
* 修改选项并单击绿色勾号（确定）或红色叉号（取消）
* 当属性页面关闭时，宏将显示消息并显示结果（确定或取消）

### VBA宏

* 创建一个类模块，并将其命名为*CommandRunManager*。复制以下代码：

{% code-snippet { file-name: CommandRunManager.vba } %}

* 将以下代码复制到主模块（包含*main*函数的模块）中
* 如果需要，修改*RunCommand*以传递任何其他命令ID。如果命令已使用确定按钮关闭，则该方法返回True；如果命令已取消，则返回False。

{% code-snippet { file-name: Macro.vba } %}

### C&#35;

不建议在.NET语言（如C#或VB.NET）中使用DoEvents函数来模拟异步操作。最好使用[使用async和await进行异步编程](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/async/)。

下面的示例演示了RunCommand的异步版本的实现，可以在不锁定UI线程的情况下等待：

**SldWorksExtension.cs**

{% code-snippet { file-name: SldWorksExtension.cs } %}

可以从任何异步方法调用该扩展。例如：

{% code-snippet { file-name: Console.cs } %}