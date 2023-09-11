---
layout: sw-tool
caption: Link Custom Properties To File
title: Link SOLIDWORKS custom properties from text file
description: VBA macro to link and auto-update multiple SOLIDWORKS custom properties from the external CSV/Text file into configuration or file
image: link-custom-property-file.svg
group: Custom Properties
---
此VBA宏允许将外部逗号分隔文件链接到SOLIDWORKS文件的特定配置或文件特定的自定义属性中。

CSV文件由两列组成（属性名称和属性值），没有标题。

如果单元格的值包含特殊符号**"**，则单元格的值必须在开头和结尾处加上**""**。

~~~
公司,Xarial Pty Limited
材料,"""SW-Material"""
质量,"""SW-Mass"""
~~~

> 您可以使用Excel修改这些值，并导出为逗号分隔的CSV文件，特殊符号将自动正确格式化。

> 属性名称或值中的逗号和换行符不受支持。

将**CLEAR_PROPERTIES**常量的值设置为**True**或**False**以配置在更新之前是否需要删除现有属性。

将**ALL_COMPONENTS**设置为**True**以处理装配体的所有组件。

~~~ vb
Const CLEAR_PROPERTIES As Boolean = False
Const ALL_COMPONENTS As Boolean = True
~~~

{% code-snippet { file-name: Macro.vba } %}

为了动态链接外部文本文件并在每次重建时更新属性，请使用以下宏。

将**UPDATE_ON_CSV_FILE_CHANGE_ONLY**常量的值设置为**True**或**False**，以配置是否仅在属性文本文件更改时重新加载属性或始终重新加载。

~~~ vb
Const UPDATE_ON_CSV_FILE_CHANGE_ONLY As Boolean = False
~~~

在插入宏特征时，宏将要求输入以下参数：

* 属性是否为特定配置或文件特定
* 是否在更新时清除属性
* 是否将装配体的参考组件包括在属性范围内

属性将在宏特征重建时自动更新。

{% code-snippet { file-name: MacroFeature.vba } %}