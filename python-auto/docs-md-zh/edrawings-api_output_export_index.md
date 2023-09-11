---
layout: sw-tool
title: 通过eDrawings API（无需SOLIDWORKS）批量导出文件到外部格式
caption: 批量导出到外部格式
description: 这个使用C#开发的控制台应用程序可以使用SOLIDWORKS eDrawings的免费版本通过其API将SOLIDWORKS、DXF、DWG和eDrawings文件导出为外部格式（.jpg、.tif、.bmp、.stl、.exe、.htm、.zip、.edrw、.eprt和.easm）。使用此工具不需要安装SOLIDWORKS或使用其许可证。
image: export-edrawings.svg
labels: [导出,批处理,eDrawings]

group: 导入/导出
---
这个使用C#开发的控制台应用程序可以使用SOLIDWORKS eDrawings的免费版本通过其API将SOLIDWORKS、DXF、DWG和eDrawings文件导出为外部格式（.jpg、.tif、.bmp、.stl、.exe、.htm、.zip、.edrw、.eprt和.easm）。使用此工具不需要安装SOLIDWORKS或使用其许可证。

此功能已集成到[xPort](https://cadplus.xarial.com/xport/)实用程序中。

## 运行工具

可以从命令行运行此应用程序，并使用以下参数：

* **-input** 输入目录或文件路径列表以进行处理。这些文件可以被eDrawings打开（例如SOLIDWORKS文件、CATIA、STEP、DXF/DWG等）。请参阅下面的完整列表：

![支持的输入文件](supported-formats.png){ width=250 }

* **-filter** 用于提取输入文件的过滤器，如果**-input**参数包含目录
* **-outdir** 导出结果的目录路径。如果该参数未指定，则文件将被导出到与输入文件相同的文件夹中，工具将自动创建目录（如果不存在）。
* **-format** 导出文件的格式列表。支持的格式：.jpg、.tif、.bmp、.png、.stl、.exe、.htm、.zip、.edrw、.eprt和.easm。指定.e以导出到eDrawings的相应格式（例如.sldprt导出为.eprt，.sldasm导出为.easm，.slddrw导出为.edrw）。如果未指定此参数，则文件将被导出到eDrawings。

工具应以以下格式调用：

~~~
[参数名称] 参数值1，参数值2 ... 参数值N
~~~

请参阅下面的参数示例

## 示例命令

* 从驱动器C中的*SW Drawings*和*SW Models*文件夹（包括子文件夹）中导出所有SOLIDWORKS文件（与过滤器*.sld*匹配，即扩展名以.sld开头）到*eDrawings*格式（.eprt用于零件，.easm用于装配，.edrw用于图纸）和html格式的*C:\EDRW*文件夹。

~~~
> export.exe -input "C:\SW Drawings" "C:\SW Models" -output C:\EDRW -filter *.sld* -format .e .html
~~~

* 将*C:\Models\Part.sldprt*导出为*C:\Models\Part.eprt*

~~~
> export.exe -input "C:\Models\Part.sldprt"
~~~

* 将*C:\Models*文件夹中的所有文件导出为可执行的eDrawings格式。每个文件将保存在与原始输入文件相同的文件夹中。

~~~
> export.exe -input C:\Models -format .exe
~~~

## 结果

操作进度将显示在控制台窗口中

![导出过程控制台输出](console-output.png)

根据设置创建输出文件。

## EDrawingsHost.cs

{% code-snippet { file-name: EDrawingsHost.cs } %}

## Program.cs

{% code-snippet { file-name: Program.cs } %}

源代码可在[GitHub](https://github.com/codestackdev/solidworks-api-examples/tree/master/edrawings-api/Export)上找到。