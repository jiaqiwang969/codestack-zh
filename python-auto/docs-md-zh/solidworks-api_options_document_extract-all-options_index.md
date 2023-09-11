---
layout: sw-tool
title: 将所有SOLIDWORKS文档级选项导出到Excel
caption: 导出所有文档选项到Excel
description: 该宏使用SOLIDWORKS API和反射，允许将所有文档属性导出为Excel格式
image: document-properties.png
labels: [导出, Excel, CSV, 选项]
group: 选项
---
![文档属性对话框](document-properties.png){ width=350 }

该宏导出所有文档属性（位于工具->选项->文档菜单下）

该宏利用[反射](https://docs.microsoft.com/zh-cn/dotnet/csharp/programming-guide/concepts/reflection)动态读取所有可用的用户首选项枚举，并调用相应的SOLIDWORKS API提取每个属性值。

宏将属性输出到CSV文件中，可以在Excel中打开。包括以下信息：

* 首选项组 - 数字、开关或文本
* 首选项的ID - 正在导出的确切选项
* 首选项选项 - 关于首选项的附加信息
* 值 - 首选项的当前值

请参考[System Options and Document Properties](https://help.solidworks.com/2016/english/api/sldworksapiprogguide/overview/system_options_and_document_properties.htm)文章，了解与特定首选项ID和值匹配的选项列表。

![在Excel中打开的提取的用户首选项](user-preferences-excel.png){ width=350 }

如果需要比较不同文件之间的首选项，该宏可能很有用。可以使用任何差异工具简化比较并识别差异，例如[WinMerge](https://winmerge.org/)

![两个模型的用户首选项之间的差异](diff-user-preferences.png){ width=550 }

可以通过修改宏开头的*OUT_FILE_PATH*常量来自定义文件输出位置。

~~~ cs
const string OUT_FILE_PATH = @""; //输出文件将在与SOLIDWORKS模型相同的位置创建，并命名为<模型名称>_prefs.csv
const string OUT_FILE_PATH = @"Options.csv"; //输出文件将在与SOLIDWORKS模型相同的位置创建，并命名为Options.csv
const string OUT_FILE_PATH = @"D:\Output\prefs.csv"; //文件将输出到D:\Output\prefs.csv
~~~

请参考[创建和运行VSTA宏](solidworks-api/getting-started/macros/create-vsta/)了解有关创建和添加代码到VSTA宏的信息。

## C# VSTA宏

{% code-snippet { file-name: Macro.cs } %}