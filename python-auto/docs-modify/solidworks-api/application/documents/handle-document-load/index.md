---
layout: sw-tool
title: Run VBA macro automatically on document load using SOLIDWORKS API
caption: Run Macro On Document Load
description: Macro runs VBA code (or another macro) automatically on file load using SOLIDWORKS API
image: run-macro-on-load.svg
labels: [auto run,model load event]
group: Model
---
{% youtube { id: tgRB8YtB4v4 } %}

这个VBA宏使用SOLIDWORKS API处理文档加载事件，并为每个文档运行自定义代码。

宏在后台运行，需要在每个会话中运行一次以开始监视。

可见（在自己的窗口中打开）和不可见（作为装配或绘图组件打开）的文档都可以处理。

![SOLIDWORKS文件打开对话框](file-open-dialog.png){ width=350 }

## 配置

* 创建新的宏
* 将代码复制到宏的相应模块中。VBA宏树应该类似于下面的图片：

![VBA宏树](vba-macro-tree.png){ width=250 }

* 将你的代码放入*HandlerModule*模块的*main*子程序中。将[IModelDoc2](https://help.solidworks.com/2012/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IModelDoc2.html)文档的指针作为参数传递。使用这个指针来代替[ISldWorks::ActiveDoc](https://help.solidworks.com/2012/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isldworks~activedoc.html)来正确处理不可见文档。

~~~ vb
Sub main(model As SldWorks.ModelDoc2)
    'TODO: 在这里添加你的代码
End Sub
~~~

* 可以自动在每个SOLIDWORKS会话中运行这个宏可能会很有用。请查看[在SOLIDWORKS应用程序启动时自动运行SOLIDWORKS宏](solidworks-api/getting-started/macros/run-macro-on-solidworks-start/)链接获取更多信息。

## 宏模块

启动事件监视的入口点

{% code-snippet { file-name: Macro.vba } %}

## FileLoadWatcher类模块

处理SOLIDWORKS API通知的类

{% code-snippet { file-name: FileLoadWatcher.vba } %}

## HandlerModule模块

需要为每个打开的文档运行的自定义VBA代码

{% code-snippet { file-name: HandlerModule.vba } %}