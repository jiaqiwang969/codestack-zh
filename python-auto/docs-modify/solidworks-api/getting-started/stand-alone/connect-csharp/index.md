---
title: Create C# stand-alone application for SOLIDWORKS API automation
caption: Create C# Stand-Alone Application for SOLIDWORKS
description: Guide of how to connect to SOLIDWORKS application from out-of-process (a.k.a Stand-Alone) application (e.g. Windows Forms, Windows Console) using C# and Microsoft Visual Studio
order: 1
image: proj-template.png
labels: [activator, c#, create instance, example, getobject, rot, sdk, solidworks api]
redirect-from:
  - /2018/03/create-c-stand-alone-application-for.html
---
在本教程中，我将演示如何使用C#和Microsoft Visual Studio从外部进程（即独立应用程序，如Windows Forms、Windows Console）连接到SOLIDWORKS应用程序。

有关本文中讨论的方法的更详细说明，请阅读[从独立应用程序连接到SOLIDWORKS](/solidworks-api/getting-started/stand-alone/)文章。

## 创建新项目

我将使用Microsoft Visual Studio开发环境。您可以使用任何版本的Visual Studio。相同的代码将适用于专业版、Express版或Community版。请点击此链接下载[Visual Studio](https://www.visualstudio.com/vs/community/)

1. 打开Visual Studio。
2. 开始新项目：

![在Visual Studio中创建新项目](new-project.png){ width=400 }

3. 选择项目模板。我建议从控制台应用程序项目模板开始，因为它包含最少的预生成代码：

![选择C#控制台应用程序项目模板](proj-template.png){ width=640 }

4. 添加对SolidWorks Interop库的引用。Interop库位于**SOLIDWORKS安装文件夹**\api\redist\SolidWorks.Interop.sldworks.dll（针对Framework 4.0及更高版本的项目）和**SOLIDWORKS安装文件夹**\api\redist\CLR2\SolidWorks.Interop.sldworks.dll（针对Framework 2.0和3.5的项目）。

![向项目添加程序集引用](add-ref.png){ width=320 }

对于针对Framework 4.0的项目，我建议将**[嵌入互操作类型](https://docs.microsoft.com/en-us/dotnet/framework/interop/type-equivalence-and-embedded-interop-types)**选项设置为false。
否则，在调用SOLIDWORKS API时，应用程序可能由于类型转换问题而出现不可预测的行为。

![嵌入互操作程序集的选项](embed-interop-types.png){ width=320 }

现在我们可以添加连接到SOLIDWORKS实例的代码。

## 创建或连接实例

连接到COM服务器最常见且最快的方法是使用[Activator::CreateInstance](https://msdn.microsoft.com/en-us/library/system.activator.createinstance(v=vs.110).aspx)方法。

{% code-snippet { file-name: CreateGetInstance.cs } %}

该方法将根据类型定义构造类型的实例。由于SOLIDWORKS应用程序已注册为COM服务器，我们可以通过[Type::GetTypeFromProgID](https://msdn.microsoft.com/en-us/library/system.type.gettypefromprogid(v=vs.110).aspx)方法从其程序标识符创建类型。
请阅读[从独立应用程序连接到SOLIDWORKS](/solidworks-api/getting-started/stand-alone#method-a---activator-and-progid)文章，了解此方法的限制说明。

或者，您可以使用[Marshal::GetActiveObject](https://msdn.microsoft.com/en-us/library/system.runtime.interopservices.marshal.getactiveobject(v=vs.110).aspx)方法连接到活动（已启动）的SOLIDWORKS会话。
这种方法将确保不会创建新的SOLIDWORKS实例，并且如果没有正在运行的SOLIDWORKS会话可连接，它将抛出异常。

{% code-snippet { file-name: GetInstance.cs } %}

## 通过ROT获取运行实例

为了连接到已经运行的特定SOLIDWORKS会话或能够创建多个会话，您可以使用Running Object Table（ROT）API。
有关此方法的更多详细信息，请阅读[从独立应用程序连接到SOLIDWORKS](/solidworks-api/getting-started/stand-alone#method-b---running-object-table-rot)文章。

{% code-snippet { file-name: CreateInstance.cs } %}

在上面的示例中，通过从SOLIDWORKS应用程序安装路径启动新进程来启动SOLIDWORKS的新会话。
*StartSwApp*函数需要**sldworks.exe**的完整路径作为第一个参数，并可选地指定超时时间（以秒为单位）作为第二个参数。
超时时间将确保应用程序在进程启动失败时不会被锁定。

您还可以将此调用设置为异步，并在SOLIDWORKS进程启动时在应用程序中显示一些进度指示：

{% code-snippet { file-name: StartSwAppAsync.cs } %}