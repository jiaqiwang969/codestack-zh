---
title: 使用SOLIDWORKS API管理自定义属性
caption: 自定义属性
description: 使用SOLIDWORKS API管理模型、配置和特定特征的自定义属性
labels: [自定义属性, 配置属性]
---
本节包含了在SOLIDWORKS API中利用自定义属性的宏和代码示例。

自定义属性是在SOLIDWORKS中用于存储元数据的键值对集合。自定义属性可以与模型本身、其配置或切割列表特征（如焊接或钣金）相关联。

通过[SOLIDWORKS API接口](https://help.solidworks.com/2018/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.ICustomPropertyManager.html)来管理自定义属性。

在许多情况下，当需要读取自定义属性的值（例如用于文件名、导出等）时，属性首先会从引用的配置中读取，如果在文件属性中找不到，则会使用文件属性。这类似于属性用于填充物料清单表的方式。

下面的代码演示了如何在代码中实现这种做法。

{% code-snippet { file-name: GetPropertyValue.vba } %}