---
layout: sw-tool
title: 使用SOLIDWORKS API对文件和配置特定的自定义属性进行排序
caption: 排序自定义属性
description: 使用SOLIDWORKS API通过逻辑顺序对文件和配置特定的自定义属性进行排序的VBA宏
image: sort-custom-properties.svg
labels: [排序, 自定义属性, 冒泡]
group: 自定义属性
---
![排序后的自定义属性](sorted-custom-properties.png){ width=350 }

这个VBA宏使用SOLIDWORKS API按照逻辑顺序对文件和所有配置的自定义属性进行排序。可以指定升序和降序两种排序方式。

逻辑顺序按照以下方式对元素进行排序。这是Windows文件资源管理器中文件的排序顺序：

* 属性1
* 属性2
* 属性3
* 属性12
* 属性20
* 属性21
* 属性30

而对于上述序列的字母排序将产生以下结果：

* 属性1
* 属性12
* 属性2
* 属性20
* 属性21
* 属性3
* 属性30

## 配置

可以通过更改宏中的常量值来配置宏，如下所示：

~~~ vb
Const ASCENDING As Boolean = True 'True表示升序排序，False表示降序排序
Const REORDER_GENERAL_CUST_PRPS As Boolean = True 'True表示对文件特定的自定义属性进行排序，False表示跳过
Const REORDER_CONF_CUST_PRPS As Boolean = True 'True表示对配置特定的自定义属性进行排序（对于零件和装配体），False表示跳过
~~~

观看[演示视频](https://youtu.be/jsjN8zNRTuc?t=97)

{% code-snippet { file-name: Macro.vba } %}