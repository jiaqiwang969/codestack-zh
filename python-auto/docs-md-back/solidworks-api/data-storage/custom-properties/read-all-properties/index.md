---
title: Read custom properties from file, configuration and cut-list elements using SOLIDWORKS API
caption: Read All Properties
description: VBA example to extract all custom properties from various sources of the active document (general, configuration specific and cut-list) using SOLIDWORKS API
image: custom-properties.png
labels: [properties,cut-list,configuration]
---
![文件的自定义属性](custom-properties.png){ width=550 }

这个VBA宏示例演示了如何使用SOLIDWORKS API从所有自定义属性的所有来源中读取所有属性。这包括文件（通用）、配置特定和切割清单属性。

结果输出到SOLIDWORKS的即时窗口中，包含属性的来源、名称、值、表达式、状态和链接状态的信息。

*PrintConfigurationSpecificProperties* 的第二个参数允许指定是否需要从缓存中读取属性或需要解析属性。当需要解析表达式以在不同配置中得到不同的值时，这个选项非常重要，例如质量或体积属性。

~~~ vb
PrintConfigurationSpecificProperties swModel, False '解析配置的属性
~~~

~~~
通用属性
    属性: 描述
    值/文本表达式: Test Part
    评估值: Test Part
    已解析: True
    已链接: False
    状态: 已解析的值

配置特定属性
    A
        属性: 重量
        值/文本表达式: "SW-Mass@@A@CS-01.SLDPRT"
        评估值: 70.20
        已解析: True
        已链接: False
        状态: 缓存的值

切割清单属性
    -无切割清单-
~~~

{% code-snippet { file-name: Macro.vba } %}