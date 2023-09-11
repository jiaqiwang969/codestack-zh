---
title: 使用 SOLIDWORKS Document Manager API 添加不可见的自定义属性到模型
caption: 添加不可见的自定义属性
description: 使用 SOLIDWORKS Document Manager API 添加不可见的自定义属性到模型的 VBA 宏
labels: [不可见, 自定义属性]
---
SOLIDWORKS 模型包含几个不可见的自定义属性，例如 $PRP:"SW-文件名"，$PRP:"SW-标题"。这些属性是只读的，无法从用户界面进行修改。但是，可以使用 Document Manager API 添加新的自定义属性。该属性在自定义属性管理器页面不可用，用户或 SOLIDWORKS API 无法修改。

此 VBA 示例演示了如何为指定的模型添加不可见的自定义属性。请按照以下方式配置宏：

~~~ vb
Const FILE_PATH As String = "C:\SampleModel.SLDPRT" '要添加不可见属性的文件的完整路径
Const PRP_NAME As String = "MyProperty" '要添加的属性名称
Const PRP_VAL As String = "MyValue" '要分配的属性值
~~~

{% code-snippet { file-name: Macro.vba } %}