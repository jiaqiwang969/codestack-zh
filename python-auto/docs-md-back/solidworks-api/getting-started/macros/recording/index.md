---
title: Recording and editing macros in SOLIDWORKS
caption: Recording Macros
description: This article explains how to record the macro commands
image: macros-save-filter.png
labels: [macro, recording]
order: 2
---
SOLIDWORKS提供了一个很好的功能，可以记录用户的操作并将其转换为宏代码。

这是一个非常方便的功能，可以用于学习SOLIDWORKS API并找到所需的方法。

可以通过单击宏工具栏上的**录制**按钮来开始录制：

![宏工具栏中的录制命令](macro-toolbar.png)

在录制模式下，将记录大部分用户操作。

> 注意：并非所有命令都可以通过宏记录来录制。如果命令未被记录到，这并不意味着该命令的API不可用。

为了提高宏录制体验，请尽量减少模型视图方向的更改和选择操作，因为这些命令将被记录下来，会导致宏代码行数过多，难以阅读。

使用**暂停**按钮跳过不必要的操作录制。

录制完成后，单击**停止**按钮并选择要保存录制宏的文件。

![保存录制宏](macros-save-filter.png){ width=400 }

请注意，可以将宏保存为VBA和VSTA格式。请参考[宏类型](/solidworks-api/getting-started/macros/types)文章，了解这些宏类型之间的区别。

如果经常录制宏，建议启用*录制后自动编辑宏*选项。

![自动编辑宏录制后选项](option-edit-macro-after-recording.png){ width=350 }

这样，在宏录制完成后会自动打开编辑器，无需显式调用*工具->宏->编辑*菜单命令来编辑源代码。

以下是以VBA、C#和VB.NET语言录制的示例宏：

![以VBA录制的宏示例](sample-vba-recorded-macro.png){ width=350 }

![以C# VSTA录制的宏示例](sample-vsta-csharp-recorded-macro.png){ width=350 }

![以VB.NET VSTA录制的宏示例](sample-vsta-vb.net-recorded-macro.png){ width=350 }