---
layout: sw-tool
title: 自动为SOLIDWORKS文件分配新文件名
caption: 分配新文件名
description: 使用SOLIDWORKS API，基于引用的绘图视图或自定义属性自动为文档分配新文件名的VBA宏
image: save-as-dialog.png
labels: [新文件名,自动命名]
group: 模型
---
这个VBA宏允许根据自定义属性值或引用的绘图视图来自动设置新文件的名称，使用SOLIDWORKS API。

此宏仅适用于之前从未保存过的文件。

![文件另存为对话框](save-as-dialog.png){ width=350 }

## 配置

可以通过更改宏开头的常量的值来配置宏。

### 设置名称来源

可以通过更改*NAME_SOURCE*常量的值来设置名称的来源，它可以取以下值之一：

* DefaultDrawingViewFileName - 从绘图中视图的引用文档的标题中提取名称
* DefaultDrawingViewCustomProperty - 从绘图中默认视图的自定义属性中提取值
* CustomProperty - 从自定义属性中提取值

如果使用*DefaultDrawingViewCustomProperty*或*CustomProperty*选项，则需要在*PRP_NAME*常量中指定要从中读取值的自定义属性的名称。

~~~vb
Const NAME_SOURCE As Integer = NameSource_e.CustomProperty
Const PRP_NAME As String = "PartNo"
~~~

### 设置标题模式

宏有两种模式，可以通过*AUTO_SAVE*常量设置：

* True - 文件将自动保存到与原始模型相同的文件夹中
* False - 当手动保存时，标题将被分配并预填在*另存为*对话框中

~~~vb
Const AUTO_SAVE As Boolean = True
~~~

{% code-snippet { file-name: Macro.vba } %}