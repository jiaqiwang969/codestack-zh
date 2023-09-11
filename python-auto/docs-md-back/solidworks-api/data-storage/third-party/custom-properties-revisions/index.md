---
title: Save custom properties revisions into 3rd party storage store using SOLIDWORKS API
caption: Save Custom Properties Revisions
description: Saving custom properties revisions (snapshots) into document 3rd party storage store using SOLIDWORKS API
image: properties-snapshots-data.png
labels: [storage,3rd party,custom properties]
---
![自定义属性](custom-properties.png){ width=450 }

此示例演示了如何使用SOLIDWORKS API利用第三方存储库保存文件的自定义属性修订。

此插件使用[SwEx.AddIn](/labs/solidworks/swex/add-in/)框架构建，但也可以与其他创建插件的方法一起使用。

插件在菜单和工具栏中添加了两个按钮，并相应地提供了两个处理程序：

* TakeCustomPropertiesSnapshot - 读取自定义属性的当前状态并将其序列化到第三方存储库中
* LoadSnapshots - 加载所有修订版本并显示消息框

每个修订版本的快照存储在第三方子存储库的存储（流）中，而有关所有可用快照的信息保存在第三方存储的子流中。

## 使用说明

* 打开任何现有的SOLIDWORKS模型（零件、装配或绘图）
* 在“自定义”选项卡中添加一些自定义属性
* 从“工具\自定义属性修订”菜单中单击“TakeCustomPropertiesSnapshot”
* 修改属性并再次单击“TakeCustomPropertiesSnapshot”。如有需要，重复此步骤
* 您可以关闭并重新打开模型和SOLIDWORKS。单击“LoadSnapshots”命令。所有属性修订将显示在消息框中

![所有属性修订显示在消息框中](properties-snapshots-data.png){ width=450 }

### PropertiesSnapshot.cs

用于序列化属性和信息的结构体

{% code-snippet { file-name: PropertiesSnapshot.cs } %}

### CustomPropertiesRevisionsAddIn.cs

处理菜单命令并读取和输出数据的插件类

{% code-snippet { file-name: CustomPropertiesRevisionsAddIn.cs } %}

### CustomPropertiesRevisions.cs

用于访问存储和序列化和反序列化数据的函数

{% code-snippet { file-name: CustomPropertiesRevisions.cs } %}

### ComStorage.cs

围绕[IStorage](https://docs.microsoft.com/en-us/windows/desktop/api/objidl/nn-objidl-istorage)接口的包装器，简化了从.NET语言访问的过程

{% code-snippet { file-name: ComStorage.cs } %}

### ComStream.cs

围绕[IStream](https://docs.microsoft.com/en-us/windows/desktop/api/objidl/nn-objidl-istream)接口的包装器，简化了从.NET语言访问的过程

{% code-snippet { file-name: ComStream.cs } %}