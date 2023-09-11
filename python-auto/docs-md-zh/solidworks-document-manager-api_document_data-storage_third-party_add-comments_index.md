---
title: 使用SOLIDWORKS Document Manager API通过第三方存储库向模型添加评论
caption: 向模型流添加评论
description: 使用SOLIDWORKS Document Manager API将评论添加到第三方存储库中的模型
image: add-comment-console-output.png
labels: [存储库,评论]
---
此示例演示了如何使用SOLIDWORKS Document Manager API将用户文本评论直接存储在模型的第三方存储库中。

每个评论都存储在第三方存储库的单独子流中。可以在不加载所有评论的情况下访问特定评论。

该程序开发为控制台应用程序，有3种模式：

* 添加新评论。通过添加-add开关后跟评论内容来执行。

~~~
AddWatermark.exe C:\MyFile.sldprt -add "示例评论"
~~~

* 列出所有评论。通过添加-list开关来执行。此命令加载所有评论的名称，而不加载其内容。

~~~
AddWatermark.exe C:\MyFile.sldprt -list
~~~

* 读取特定评论。通过添加-read开关后跟评论名称来执行。在这种情况下，评论信息（文本、作者和日期）将被加载并打印到控制台。

~~~
AddWatermark.exe C:\MyFile.sldprt -read Comment3
~~~

![控制台中的输出结果](add-comment-console-output.png){ width=450 }

### Program.cs

处理命令行参数并执行相应操作的例程。

{% code-snippet { file-name: Program.cs } %}

### ComStorage.cs

封装了[IStorage](https://docs.microsoft.com/en-us/windows/desktop/api/objidl/nn-objidl-istorage)接口，简化了从.NET语言访问的过程。

{% code-snippet { file-name: ComStorage.cs } %}

### ComStream.cs

封装了[IStream](https://docs.microsoft.com/en-us/windows/desktop/api/objidl/nn-objidl-istream)接口，简化了从.NET语言访问的过程。

{% code-snippet { file-name: ComStream.cs } %}