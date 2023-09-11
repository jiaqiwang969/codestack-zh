---
layout: sw-tool
title: 使用SOLIDWORKS API根据自定义属性重命名切割清单特征
caption: 重命名切割清单特征
description: 使用SOLIDWORKS API根据自定义属性重命名切割清单特征的VBA宏（适用于钣金和焊接件）
image: cut-list-table.svg
labels: [切割清单,钣金,焊接件,重命名]
group: 切割清单
---
![钣金切割清单特征](sheet-metal-cut-list.png){ width=250 }

此VBA宏允许根据名称模板重命名焊接件和钣金零件的所有切割清单特征，名称模板可以包含文件和切割清单自定义属性、文件名、配置名和自由文本的值。

![切割清单属性](cut-list-properties.png){ width=550 }

要配置宏，请修改*NAME_TEMPLATE*、*INDEX_FORMAT*和*ALWAYS_ADD_INDEX*常量的值。

*NAME_TEMPLATE*可以包含自由文本和占位符，占位符将被相应的自定义属性值动态替换。

支持以下占位符：

* <\_FileName\_> - 零件文件的名称（不包括扩展名），切割清单所在的文件
* <\_ConfName\_> - 零件文件的活动配置名称
* <$CLPRP:[PropertyName]> - 任何切割清单属性的名称，用于读取值，例如<Thickness>将被替换为切割清单自定义属性Thickness的值
* <$PRP:[PropertyName]> - 零件的任何自定义属性的名称，用于读取值，例如<PartNo>将被替换为切割清单自定义属性PartNo的值

占位符将在运行时为每个切割清单解析。

*INDEX_FORMAT*常量允许指定特征名称的索引填充方式（如果使用名称）。默认情况下，解析为相同值的特征名称将具有第二个特征的索引，依此类推，除非将*ALWAYS_ADD_INDEX*常量设置为true。在这种情况下，第一个特征也将有索引。

例如，以下设置（如果零件PartNo等于ABC）将将切割清单特征解析为*ABC_001*、*ABC_002*、*ABC_003*等。

~~~ vb
Const NAME_TEMPLATE = "<$PRP:PartNo>_"
Const INDEX_FORMAT As String = "000"
Const ALWAYS_ADD_INDEX As Boolean = True
~~~

观看[视频演示](https://youtu.be/jsjN8zNRTuc?t=200)

{% code-snippet { file-name: Macro.vba } %}