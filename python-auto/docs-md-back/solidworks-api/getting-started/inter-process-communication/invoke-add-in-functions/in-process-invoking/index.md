标题：从外部进程应用程序中调用SOLIDWORKS插件API的过程中调用
说明：调用插件API的框架，以从独立应用程序或宏中获得最佳性能
图片：macro-solution-tree.png
标签：[插件API，异步，性能，内部调用]
顺序：4

独立自动化COM基础应用程序自动化（包括SOLIDWORKS）的主要限制之一是性能。

当需要从外部进程应用程序调用数百个API调用时，性能可能下降数百甚至数千倍，与内部调用相比。

在以下任何方法中调用插件API时，也会出现完全相同的限制：[通过插件对象](/solidworks-api/getting-started/inter-process-communication/invoke-add-in-functions/via-add-in-object/)，[通过运行对象表](/solidworks-api/getting-started/inter-process-communication/invoke-add-in-functions/via-rot/)等。

人们可能错误地认为插件内部的所有SOLIDWORKS API调用都是通过内部调用的，因为只有一个API函数从独立应用程序中调用。但实际上，SOLIDWORKS插件中的所有SOLIDWORKS API调用都是作为外部调用调用的。这意味着调用插件API将导致与调用独立应用程序相同的性能损失。

然而，有一种方法可以最大限度地提高性能，并通过从外部进程应用程序调用来获得与内部调用相同的结果。

以下插件示例实现了一个函数，用于索引活动装配文档的所有面。

插件使用[SwEx.AddIn Framework](/labs/solidworks/swex/add-in/)开发，但相同的技术也适用于使用不同方法构建的插件。

它遍历所有组件、所有实体和所有面，并在跟踪窗口中输出有关面的一些信息。

插件具有一个菜单命令，允许在进程中调用其函数。

![调用面索引插件的菜单](face-indexer-menu.png){ width=350 }

完成后，将显示带有结果的消息框。

![调用插件命令的结果](add-in-result.png){ width=300 }

## FaceIndexer插件
这是一个实现SOLIDWORKS插件和API对象接口的主要项目。

### FaceIndexerAddIn.cs

插件类

{% code-snippet { file-name: face-indexer/FaceIndexerAddIn.cs } %}

### FaceIndexerAddInApi.cs

API对象定义。

{% code-snippet { file-name: face-indexer/FaceIndexerAddInApi.cs } %}

该插件为第三方提供API。*IndexFaces*方法是一个外部进程的API调用，可以使用以下代码片段：

~~~ cs
var count = addIn.IndexFaces(assm);
Console.WriteLine($"已索引{count}个面");
~~~

结果性能几乎下降了一百倍：

![从独立应用程序调用插件API的结果](stand-alone-result.png){ width=300 }

使用[SolidWorks.Interop.sldworks.ISldWorks.CommandInProgress](https://help.solidworks.com/2016/English/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.ISldWorks~CommandInProgress.html) SOLIDWORKS API属性可以稍微改善一些，但与基准结果相比，性能仍然下降了十多倍。

~~~ cs
app.CommandInProgress = true;
var count = addIn.IndexFaces(assm);
app.CommandInProgress = false;
Console.WriteLine($"已索引{count}个面");
~~~

下面是结果的比较表。结果可能因装配的大小和使用的API调用而异。

| 环境                           | 结果（秒） | 比率（%） |
|---------------------------------|-----------------|----------|
| 插件内部调用               | 2.63            | 1        |
| 独立应用程序                     | 241.95          | 92       |
| 独立应用程序命令进行中 | 36.14           | 13.74    |
| VBA宏                       | 2.57            | 0.98     |
| VBA宏内部调用   | 2.20            | 0.84     |
| 独立应用程序内部调用 | 1.77            | 0.67     |

当从独立应用程序中以内部调用的方式调用插件API时，可以获得最佳性能。通过提供延迟调用来索引面，可以实现此功能。此调用将将请求放入队列并立即返回控制权。然后，请求将在插件中处理。可以使用[OnIdle](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.dsldworksevents_onidlenotifyeventhandler.html) SOLIDWORKS API通知来处理队列。由于此事件在进程中处理，实际的API调用也将在进程中处理。

还重要的是注册回调函数，插件可以调用该函数通知独立应用程序操作已完成。

下面是一个示例，展示了独立应用程序以内部调用的方式调用插件API。

## 独立应用程序

调用插件函数的C#应用程序。

### FaceIndexerCallback.cs

回调函数，用于在内部调用完成时通知独立应用程序。必须将其注册为COM对象。

{% code-snippet { file-name: stand-alone/FaceIndexerCallback.cs } %}

### Program.cs

控制台应用程序调用插件API的内部调用，并在回调中等待结果。

{% code-snippet { file-name: stand-alone/Program.cs } %}

它也可以从宏或任何其他类型的应用程序中调用。

## VBA宏

调用插件API的VBA宏。在此示例中，使用用户窗体使宏保持运行，直到调用回调函数。

![VBA宏中的项目树](macro-solution-tree.png){ width=250 }

### 宏模块

启动用户窗体的主模块

{% code-snippet { file-name: Macro.vba } %}

### FaceIndexerCallback类模块

接收完成通知的回调类的实现

{% code-snippet { file-name: FaceIndexerCallback.vba } %}

### Form1窗体

连接到插件并调用其API的用户窗体

{% code-snippet { file-name: Form1.vba } %}

源代码可从[GitHub](https://github.com/codestackdev/solidworks-api-examples/tree/master/swex/add-in/face-indexer)下载。