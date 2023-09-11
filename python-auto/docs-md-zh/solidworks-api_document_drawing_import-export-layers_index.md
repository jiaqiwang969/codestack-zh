---
layout: sw-tool
caption: 导入/导出图层
title: 从SOLIDWORKS图纸中导入和导出所有图层的宏到文本文件
description: VBA宏用于导入和导出SOLIDWORKS图纸中图层的信息（描述、颜色、样式、厚度、可见性和打印）
image: import-export-drawing-layers.svg
group: 图纸
---
![SOLIDWORKS图纸中的图层](sw-layers.png){ width=600 }

这些宏允许将SOLIDWORKS图纸中的图层信息导入和导出到文本文件中。

导入和导出的信息如下：

* 名称
* 描述
* 可见性
* 是否打印
* 颜色
* 样式
* 厚度

## 格式

此宏将所有信息以以下格式导出到输出文本文件中

~~~
图层: 实体
    描述: 带有实体的图层
    颜色: 0 128 255
    可打印: 是
    样式: 0
    可见: 是
    厚度: 5

图层: 品牌
    描述: 用于品牌图片的图层
    颜色: 0 128 128
    可打印: 是
    样式: 0
    可见: 是
    厚度: 0
~~~

默认情况下，文件将保存或加载到与原始文件相同的文件夹中，文件名前缀为**_Layers.txt**

## CAD+

此宏与[Toolbar+](https://cadplus.xarial.com/toolbar/)和[Batch+](https://cadplus.xarial.com/batch/)工具兼容，因此可以将按钮添加到工具栏并分配快捷键以便更轻松地访问或批量运行。

要启用[宏参数](https://cadplus.xarial.com/toolbar/configuration/arguments/)，请将**ARGS**常量设置为true

~~~ vb
#Const ARGS = True
~~~

将路径设置为导入或导出的文本文件作为宏参数。

## 导出

{% code-snippet { file-name: Export.vba } %}

## 导入

{% code-snippet { file-name: Import.vba } %}