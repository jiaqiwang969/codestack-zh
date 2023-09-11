标题：使用SOLIDWORKS API在模型第三方存储中进行树结构序列化
说明：使用SOLIDWORKS API和模型文档中的XmlSerializers示例，展示了如何使用第三方存储（流）来序列化和反序列化树结构。
图片：read-data-result.png
标签：[序列化，第三方存储]

这个示例演示了如何在SOLIDWORKS API中使用第三方存储来直接读取和写入自定义结构。

示例SOLIDWORKS插件使用[SwEx.AddIn](/labs/solidworks/swex/add-in/)框架构建，但也可以与其他创建插件的方法一起使用。

插件在菜单和工具栏中添加了两个按钮，并相应地提供了两个处理程序：

- SaveTree - 异步方法，用于将数据存储在流中。每次保存后，此方法会增加结构的版本。
- LoadTree - 从流中加载数据，并显示根元素的名称和版本。

![从流中读取的数据显示的结果](read-data-result.png){ width=250 }

## 使用说明

- 打开任何模型
- 点击“保存数据”按钮。将第一个版本的结构与模型一起保存
- 您可以关闭模型和SOLIDWORKS
- 重新打开模型，然后点击“加载数据”。保存的结构信息将显示在消息框中
- 再次点击“保存数据”按钮。数据版本将更新

在Visual Studio项目设置中，需要设置“允许不安全代码”选项：

![C#项目中的允许不安全代码选项](vs-setting-allow-unsafe-code.png){ width=450 }

**TreeSerializerAddIn.cs**

{% code-snippet { file-name: TreeSerializerAddIn.cs } %}

此示例中使用的结构表示简单的分层数据。

**ElementsTree.cs**

{% code-snippet { file-name: ElementsTree.cs } %}

为了简化，将[IStream](https://docs.microsoft.com/en-us/windows/desktop/api/objidl/nn-objidl-istream) COM流封装到[System.IO.Stream](https://docs.microsoft.com/en-us/dotnet/api/system.io.stream?view=netframework-4.7.2)类型中。

**ComStream.cs**

{% code-snippet { file-name: ComStream.cs } %}

序列化和反序列化过程利用[XmlSerializer](https://docs.microsoft.com/en-us/dotnet/api/system.xml.serialization.xmlserializer?view=netframework-4.7.2)类，但也可以使用其他序列化方法。

**TreeSerializer.cs**

{% code-snippet { file-name: TreeSerializer.cs } %}