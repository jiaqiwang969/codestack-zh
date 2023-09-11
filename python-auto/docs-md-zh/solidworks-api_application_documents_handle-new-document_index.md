---
layout: sw-tool
title: 在SOLIDWORKS API中创建新文档时运行宏
caption: 在新文档创建时运行宏
description: 使用SOLIDWORKS API在每次创建新文档时运行其他宏或代码的VBA宏
image: new-document.png
labels: [新文档]
group: 模型
---
![在SOLIDWORKS中创建新文档](new-document.png){ width=350 }

这个VBA宏处理在SOLIDWORKS中创建新文档（零件、装配或图纸）的过程，使用SOLIDWORKS API，并允许在此事件发生时自动运行自定义代码或另一个宏。此宏还处理在SOLIDWORKS装配中创建新虚拟文档的情况。

## 配置

* 创建新的宏（例如*RunOnNewDocCreated.swp*）
* 将代码复制到宏的相应模块中。VBA宏树应该类似于下面的图片：

![宏文件树](macro-tree.png){ width=250 }

* 将代码放入*HandlerModule*模块的*main*子程序中。将[IModelDoc2](https://help.solidworks.com/2012/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IModelDoc2.html)文档的指针作为参数传递。在此事件到达时，使用此指针而不是[ISldWorks::ActiveDoc](https://help.solidworks.com/2012/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isldworks~activedoc.html)，因为新文档可能还没有设置为活动文档。

~~~ vb
Sub main(model As SldWorks.ModelDoc2)
    'TODO: 在这里添加你的代码
End Sub
~~~

* 可以在每个SOLIDWORKS会话中自动运行此宏可能会很有用。有关更多信息，请参阅[在SOLIDWORKS启动时自动运行宏](solidworks-api/getting-started/macros/run-macro-on-solidworks-start/)链接。
* 要了解如何运行另一个宏或一组宏，请参考[运行一组宏](/solidworks-api/application/frame/run-macros-group/)文章

## 宏模块

启动新文档创建事件监视的入口点

{% code-snippet { file-name: Macro.vba } %}

## FileNewWatcher类模块

处理SOLIDWORKS新文档API通知的类

{% code-snippet { file-name: FileNewWatcher.vba } %}

## HandlerModule模块

需要为每个新创建的文档运行的自定义VBA代码

{% code-snippet { file-name: HandlerModule.vba } %}