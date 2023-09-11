---
layout: sw-tool
title: 使用SOLIDWORKS API运行一组宏的宏
caption: 运行一组宏
description: 该宏演示了如何使用SOLIDWORKS API在一个宏中运行一组宏
image: macros-library.png
labels: [宏, 运行组]
group: 框架
---
![Windows文件夹中的宏库](macros-library.png)

可以使用[SOLIDWORKS API函数ISldWorks::RunMacro2](https://help.solidworks.com/2010/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isldworks~runmacro2.html)从另一个宏中运行宏。

这样可以在一个宏中运行多个宏。当在宏工具栏上[添加自定义宏按钮](/solidworks-api/getting-started/macros/macro-buttons/)时，这非常有用，因为可以通过一个按钮点击执行多个命令。

以下示例允许在一个宏中运行多个SOLIDWORKS宏。

{% code-snippet { file-name: Macro-simple.vba } %}

更改**RunMacro**调用的参数以调用您自己的一组宏。

~~~ vb
RunMacro "宏的完整路径", "模块名称", "入口函数名称"
~~~

其中

![宏入口点](macro-entry-point.png){ width=350 }

* **宏的完整路径** - VBA或VSTA宏的完整路径，.swp或.dll文件[/solidworks-api/getting-started/macros/types)
* <span style="color:blue">**模块名称**</span> - 定义主入口函数的模块名称。通常是宏名称后跟1。
* <span style="color:green">**入口函数名称**</span> - 入口函数的名称。此函数不能有参数。通常命名为**main**

> 根据需要修改宏。您可以添加或删除对**RunMacro**的调用，并更改路径、模块和函数名称以匹配库中宏的路径

以下宏提供了更高级的运行宏功能。它允许指定多个逗号分隔的宏以及使用完整路径或相对路径的文件夹。

这样可以更好地维护宏。

此宏还处理以下错误：

* 当找不到指定的宏路径时：

![找不到宏错误](macro-not-found-error.png){ width=250 }

* 当无法运行宏时（例如宏损坏）

![无法运行宏错误](failed-to-run-macro-error.png){ width=250 }

要配置宏，需要修改**MACROS_PATH**变量的值：

* 可以通过逗号分隔它们来指定要运行的多个宏，例如**Macro1.swp, Macro2.swp**
* 可以使用完整路径（例如**D:\Macros\Macro1.swp**）或使用相对路径（例如**Macro1.swp**）指定宏。如果后者，宏必须与此主宏位于同一文件夹中
* 可以指定要运行的宏所在的文件夹（例如**D:\Macros**或**Macros**）。与宏路径一样，接受完整路径或相对文件夹路径。在这种情况下，将运行指定文件夹中的所有宏
* 如果指定空字符串，即 

~~~ vb
Const MACROS_PATH As String = " "
~~~

将运行放置此主宏的文件夹中的所有宏。此选项非常有用，因为只需将主宏复制到宏库的位置即可运行，无需修改它。

{% code-snippet { file-name: Macro.vba } %}