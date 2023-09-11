标题：通过剪贴板将参数传递给SOLIDWORKS VBA宏
说明：通过剪贴板
描述：从.NET应用程序或另一个宏通过剪贴板将自定义字符串参数传递给VBA宏
图片：msg-box-macro-argument.png
标签：[参数，剪贴板，示例，参数，solidworks api]
重定向自：
  - /2018/04/pass-arguments-to-vba-macro-via-clipboard.html
---
系统剪贴板可以存储不同类型的数据（包括但不限于文本、图像、HTML等）。最简单的方法是将自定义参数写入文本缓冲区，但这将清除缓冲区中已有的所有数据（如果有的话）。这可能会引起混淆，并导致用户体验不佳，因为运行宏可能会覆盖已复制到剪贴板的文本。

另一种方法是将数据写入具有唯一名称的自定义缓冲区，以便它不会明确地暴露给用户，并且只能通过代码访问。

让我们从“目标”宏开始，该宏将从不同的“主”宏中调用。

{% code-snippet { file-name: read-argument-from-vba.vba } %}

上面的示例中，从“主”宏传递的参数值将在“目标”宏中提取并显示给用户的消息框中：

![宏中显示传递的参数值的消息框](msg-box-macro-argument.png){ width=400 height=132 }

助手类从**__SwMacroArgs__**格式中读取缓冲区值。这是一个已知于“主”宏（将写入参数值）和“目标”宏（将读取值）的自定义名称。如果需要，可以将其重命名为任何其他自定义名称。

{% code-snippet { file-name: argument-helper-get-argument.vba } %}

为了调用宏并传递参数，需要将**__SwMacroArgs__**格式的缓冲区值设置为Unicode字符串。以下是演示如何在不同的编程语言中实现此目的的示例：

<details>
<summary>VBA宏</summary>

参数助手模块

{% code-snippet { file-name: argument-helper-set-argument.vba } %}

宏

{% code-snippet { file-name: call-macro-with-argument-vba.vba } %}

</details>

<details>
<summary>C#</summary>

{% code-snippet { file-name: call-macro-with-arguments-csharp.cs } %}

</details>

<details>
<summary>VB.NET</summary>

{% code-snippet { file-name: call-macro-with-arguments-vb.net.vb } %}

</details>

> 注意：上述示例不处理“竞争条件”（当多个具有不同参数的宏可能并行运行时）。使用互斥体或信号量对象来同步对共享资源的访问。