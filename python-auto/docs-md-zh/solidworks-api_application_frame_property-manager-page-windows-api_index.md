---
caption: 使用Windows API配置属性管理器页面
title: 使用Windows API运行和配置SOLIDWORKS命令
description: 示例演示如何使用Windows API调用和配置SOLIDWORKS绘图中的插入模型项命令
image: insert-model-items-property-manager-page.png
---

在某些情况下，某些SOLIDWORKS功能或选项可能无法在SOLIDWORKS API命令中使用或可能无法正常工作。

在这种情况下，如果其他解决方法不可用，可以使用Windows API来调用和配置命令。

此示例演示了如何使用Windows API将模型尺寸插入到SOLIDWORKS绘图视图中。此示例模拟了[IDrawingDoc::InsertModelAnnotations3](https://help.solidworks.com/2015/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.idrawingdoc~insertmodelannotations3.html) API方法的功能。

![模型项属性管理器页面](insert-model-items-property-manager-page.png){ width=400 }

这是一个C#控制台应用程序，它接受绘图文件的路径作为输入参数。将执行以下步骤：

* 连接或创建SOLIDWORKS的新实例
* 打开指定的绘图文件
* 使用SOLIDWORKS API运行命令打开**插入模型项**属性管理器页面
* 迭代所有控件，并将源设置为**整个模型**和**包括隐藏特征的项**选项
* 点击确定按钮关闭属性管理器页面
* 保存并关闭文档

在调用Windows API时，需要开发一种查找特定控件和命令ID的策略。

Microsoft内置在Visual Studio中的Spy++实用程序可以是分析Windows控件的有用工具：

![带有属性管理器页面Win32控件列表的Spy++界面](spy-plus-plus-solidworks-window.png){ width=400 }

有关此方法的更多信息，请参阅[调用Windows API命令](https://blog.codestack.net/missing-solidworks-api-command#calling-windows-command)博文。

## 限制

* 低级代码，可读性较差且更复杂
* 在某些情况下，控件没有永久ID，因此需要使用额外的逻辑，例如控件标题或顺序，这可能会因会话到会话、版本到版本或区域设置而异
* Windows API执行低级调用，因此在处理内存、释放指针等方面需要小心，否则可能会导致意外行为。阅读Windows API文档以获取有关特定API调用的更多信息
* 操作的结果没有反馈（仅有低级API结果），这意味着很难确定操作是否成功执行。操作还可能产生需要单独处理的模型弹出窗口。

{% code-snippet { file-name: Console.cs } %}