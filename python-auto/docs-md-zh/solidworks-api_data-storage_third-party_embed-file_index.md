---
title: 使用SOLIDWORKS API在模型第三方存储中序列化文件内容
caption: 将文件嵌入第三方存储
description: 使用SOLIDWORKS API和模型文档中的XmlSerializers示例，以VB.NET展示如何使用第三方存储（流）嵌入和提取文件内容
image: embed-file-menu.png
labels: [序列化,第三方存储,文件]
---
本示例演示了如何使用SOLIDWORKS API中的第三方存储将文件内容直接嵌入和提取到模型流中。

示例SOLIDWORKS插件使用[SwEx.AddIn](/labs/solidworks/swex/add-in/)框架构建，但也可以与其他创建插件的方法一起使用。

插件在菜单和工具栏中添加了两个按钮，并相应地提供了两个处理程序：

![插件菜单](embed-file-menu.png){ width=400 }

* AddFile - 异步方法，用于将嵌入文件数据存储到流中。该方法要求用户选择文件，读取其内容并将其序列化为文件流。
* LoadFile - 从流中加载嵌入的文件，并提示用户选择文件路径以存储内容。文件名基于嵌入的文件名进行预填充。

![浏览保存文件路径](select-save-path.png){ width=550 }

## 使用说明

* 打开任何模型（模型必须保存到磁盘）
* 点击"AddFile"按钮。将显示文件浏览对话框。选择任意文件。文件数据将被序列化到模型中，并显示消息框。
* 您可以关闭模型和SOLIDWORKS
* 重新打开模型并点击"LoadFile"。文件数据将从模型中反序列化，并显示文件另存为对话框（文件名基于嵌入的文件名填充）。文件将保存到所选位置。

**EmbedFileAddIn.vb**

{% code-snippet { file-name: EmbedFileAddIn.vb } %}

用于序列化的结构包含文件的内容和文件名

**EmbedFileData.vb**

{% code-snippet { file-name: EmbedFileData.vb } %}

为了简化，将[IStream](https://docs.microsoft.com/en-us/windows/desktop/api/objidl/nn-objidl-istream) COM流封装到[System.IO.Stream](https://docs.microsoft.com/en-us/dotnet/api/system.io.stream?view=netframework-4.7.2)类型中。

**ComStream.vb**

{% code-snippet { file-name: ComStream.vb } %}

使用[XmlSerializer](https://docs.microsoft.com/en-us/dotnet/api/system.xml.serialization.xmlserializer?view=netframework-4.7.2)类进行序列化和反序列化，但也可以使用其他序列化方法。

**EmbedFile.vb**

{% code-snippet { file-name: EmbedFile.vb } %}