---
title: 使用SOLIDWORKS文档管理器API读取所有自定义属性
caption: 读取所有属性
description: 使用SOLIDWORKS文档管理器API，通过VBA宏从所有来源（文件、配置、切割列表）读取所有自定义属性。
image: properties-list.png
labels: [读取属性,自定义属性]
---
![SOLIDWORKS自定义属性](properties-list.png){ width=550 }

这个VBA宏演示了如何使用SOLIDWORKS文档管理器API从所有来源（通用文件属性、配置特定属性和切割列表项属性）读取所有自定义属性。

所有结果以以下格式输出到VBA编辑器的即时窗口中。

~~~
通用自定义属性
    属性：ApprovedDate
    值/文本表达式：12/09/2019
    评估值：12/09/2019
    类型：日期

配置特定属性
    B
        属性：ApprovedDate
        值/文本表达式：12/09/2019
        评估值：12/09/2019
        类型：日期

    A
        属性：ApprovedDate
        值/文本表达式：12/09/2019
        评估值：12/09/2019
        类型：日期

切割列表属性
    B
            属性：Bounding Box Length
            值/文本表达式："SW-Bounding Box Length@@@Sheet<1>@Part3.SLDPRT"
            评估值：100
            类型：文本
...

    A
            属性：Bounding Box Length
            值/文本表达式："SW-Bounding Box Length@@@Sheet<1>@CS-02.SLDPRT"
            评估值：150
            类型：文本
...
~~~

在*FILE_PATH*常量中指定文件的完整路径。

{% code-snippet { file-name: Macro.vba } %}