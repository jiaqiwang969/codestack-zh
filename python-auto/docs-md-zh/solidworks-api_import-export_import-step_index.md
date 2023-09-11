---
layout: sw-tool
title: 使用子文件夹将STEP文件导入并保存为SOLIDWORKS文件的宏
caption: 导入STEP文件
description: 使用子文件夹将STEP文件导入并保存为SOLIDWORKS文件的VBA宏。
image: import-step-icon.svg
labels: [STEP, 导入, 批处理+]
group: 导入/导出
---
作者：[Eddy Alleman](https://www.linkedin.com/in/eddyalleman/) ([EDAL Solutions](https://www.edalsolutions.be/index.php/en/))

![用于导入STEP文件的选项](import-step-options.png){ width=400 }

## 上下文情境：

假设我们有数百个STEP文件，都在供应商的同一个文件夹中。
我们想要建立一个库，以便在设计中反复重用它们。
为了将文件彼此分开，我们希望每个STEP文件都导出到一个单独的文件夹中。

## SOLIDWORKS有一个工具可以实现这个目标：任务计划程序

![任务计划程序导入](task-scheduler-import.png){ width=350 }

但是，除非我们首先将STEP文件放入单独的文件夹中，然后将导出的SOLIDWORKS文件保存到这些子文件夹中，否则所有的STEP文件都将保存在同一个文件夹中。
这需要大量的手动工作。

此外，我们无法确定是否存在重复文件以及这些文件是否具有不同的详细级别。
我们希望在导入后能够选择最好的文件，而不仅仅是覆盖已处理的文件。

那么，我们如何自动化这个过程，避免手动创建所有这些子文件夹呢？

## 使用简单宏的批处理+

批处理+是CAD+的一部分，是一个免费工具，它处理批处理文件时处理了许多特殊情况。
我们选择这个选项是因为它易于设置，并且可以完全控制整个过程。

以下宏确定了STEP文件是装配件还是零件文件。
如果是装配件，则组件将保存为单独的零件文件（取决于系统选项，请参见上面的图像）。

该宏在与STEP文件相同的位置创建一个子文件夹，并使用相同的名称。
这有助于将属于同一组的文件与其他导入文件分开。
如果您不每次都将它们放在新文件夹中，可能会得到相同的文件两次，并且最后一次保存会覆盖之前的文件。在这种情况下，请确保它们是相同的。

## 先决条件

（1）确保您的系统选项未设置为：
    提示用户选择文档模板
    而是使用："始终使用这些默认文档模板"
否则，SolidWorks会一直要求选择文档模板。

（2）设置系统选项 > 导入 > 启用3D互连关闭
    关于3D互连的文档：
    直接将专有CAD数据插入到SOLIDWORKS装配中，而无需将其转换为SOLIDWORKS文件。
    而我们正是要进行转换。3D互连只是创建了一个指向STEP文件的链接，并在需要时进行更新。

![在批处理+中使用的设置](batch-plus-settings.png){ width=800 }

{% code-snippet { file-name: Macro.vba } %}