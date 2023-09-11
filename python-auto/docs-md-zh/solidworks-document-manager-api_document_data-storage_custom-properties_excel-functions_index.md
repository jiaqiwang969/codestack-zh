---
layout: sw-tool
title: 使用Excel宏管理SOLIDWORKS文件中的自定义属性
caption: 在Excel中管理属性
description: 这个Excel宏可以通过Excel电子表格批量快速地读取和写入SOLIDWORKS文件中的自定义属性
image: excel-custom-properties.svg
labels: [dm, excel, custom properties]
group: 自定义属性
---
![在Excel中的SOLIDWORKS自定义属性](excel-custom-properties.svg){ width=250 }

这个Excel VBA宏为Excel调色板添加了额外的功能，可以从SOLIDWORKS文件中读取和写入自定义属性。

这个宏利用了文档管理器，使得读取和写入属性的过程比常规的SOLIDWORKS API快得多（10倍到100倍以上）。

此外，使用这个宏不需要安装SOLIDWORKS。

## 准备工作

* 如果您没有文档管理器许可证密钥，请按照[激活文档管理器](/solidworks-document-manager-api/getting-started/create-connection#activating-document-manager)文章中的步骤获取文档管理器许可证。这个密钥对于订阅SOLIDWORKS的客户是免费的。
* 创建一个新的Excel文档并创建一个新的宏。将下面的宏代码粘贴到宏中。

{% code-snippet { file-name: Macro.vba } %}

* 修改宏并在第一步中获取的许可证密钥的位置输入许可证密钥。注意，根据密钥的大小，您可能会看到“编译错误：无效的过程外错误”的错误。请参考[这篇文章](/solidworks-api/troubleshooting/macros/too-long-vba-macro-line/)找到解决方案。

~~~ vb jagged-bottom
Const SW_DM_KEY As String = "<Your License Key>"
~~~

* 在宏中添加*SwDocumentMgr YEAR Type Library*引用。

![在宏中添加文档管理器引用](sw-document-manager-reference.png)

## 使用方法

{% youtube id: a068ht0rDQQ %}

宏将在Excel函数范围内添加2个函数，可以像其他函数一样在Excel中使用。

![在列表中添加的Excel函数](excel-function.png)

作为标准函数，用户可以将参数作为对其他单元格的引用传递。

![设置产品ID属性的值](setting-single-property.png)

或者可以使用自由文本。

![从文件的默认配置中读取描述属性](reading-description-config-property.png)

当需要写入或读取多个属性时，使用Excel范围来最大化操作的性能。

![批量更新多个文件的3个属性](batch-set-properties.png)

### GETSWPRP

这个函数允许从文件或给定的配置中提取指定属性的值。如果尝试读取不存在的属性，将抛出错误。

#### 参数

* 文件名 - SOLIDWORKS零件、装配体或图纸的完整路径
* 属性名称 - 要从中读取值的属性或属性范围
* （可选）配置名称 - 要从中读取值的配置的名称，如果未指定，则从常规选项卡中读取属性

### SETSWPRP

将属性写入指定的SOLIDWORKS文件中的指定配置。如果属性已存在，则更新现有属性；如果不存在，则创建新属性。

#### 参数

* 文件名 - SOLIDWORKS零件、装配体或图纸的完整路径
* 属性名称 - 要将值写入的属性或属性范围
* 属性值 - 属性的值或值范围
* （可选）配置名称 - 要将值写入的配置的名称，如果未指定，则写入到常规选项卡中的属性

## 故障排除

如果发生错误，相应的单元格将指示错误：

![单元格中的计算错误](cell-error.png)

要了解更多关于错误的信息，请打开宏并检查即时窗口输出。

![在VBA即时窗口中显示的错误](immediate-window-error.png)

打开的错误代码的描述可以在[这里](https://help.solidworks.com/2015/English/api/swdocmgrapi/SolidWorks.Interop.swdocumentmgr~SolidWorks.Interop.swdocumentmgr.SwDmDocumentOpenError.html)找到。

> 强烈建议在使用这个宏之前在样本数据上进行测试。在使用这个宏之前，强烈建议备份数据。

## 注意事项

这个宏将提取公式（而不是解析后的值）作为具有方程式（如质量或材料）的属性。

要定义公式，请使用""来保护"符号。例如

~~~
=SETSWPRP(A2, "Mass", """SW-Mass@Part1.SLDPRT""")
~~~