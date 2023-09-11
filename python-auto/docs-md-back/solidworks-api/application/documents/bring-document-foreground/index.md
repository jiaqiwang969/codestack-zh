---
title: 使用SOLIDWORKS API将文档置于前景（激活文档）
caption: 将文档置于前景（激活文档）
description: 本示例演示了如何使用[SOLIDWORKS API的ISldWorks::ActivateDoc3](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isldworks~activatedoc3.html)方法将通过路径选择的文档置于前景（激活）。

文档可以以两种状态打开（可见或隐藏）。隐藏的文档通常是从装配或绘图的组件中加载到内存中的模型。在这种情况下，当调用[ISldWorks::OpenDoc6](https://help.solidworks.com/2017/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isldworks~opendoc6.html)方法时，文档不会自动置于前景。关闭作为组件加载的文档时也是类似的情况：文档将变为不可见而不是关闭。

* 在没有打开文件的情况下运行宏 - 文件将被打开并关闭
* 打开装配体并运行宏。在这种情况下，[ISldWorks::OpenDoc6](https://help.solidworks.com/2017/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isldworks~opendoc6.html) API不会强制将零件置于前景，因此需要强制激活它。

[下载示例文件](SimpleBox.zip)

{% code-snippet { file-name: Macro.vba } %}