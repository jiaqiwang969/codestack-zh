---
title: 使用 SOLIDWORKS PDM API 列出保险库中的所有变量
caption: 列出所有变量
description: 使用 VBA 宏在指定的保险库中使用 SOLIDWORKS PDM API 列出所有变量名称和 ID
image: pdm-variables.png
labels: [变量, 列表]
---
![PDM 变量列表 SOLIDWORKS PDM 管理面板](pdm-variables.png)

这个 VBA 宏使用 SOLIDWORKS PDM API 列出了指定保险库中的所有变量。变量名称和 ID 以以下格式输出到 VBA 编辑器的即时窗口中：

~~~
Album(102)
Approved by(53)
Approved On(46)
Artist(101)
Assembly No.(67)
Attachments(92)
Author(55)
Body(91)
BOM Quantity(106)
Checked by(58)
Checked Date(62)
~~~

{% code-snippet { file-name: Macro.vba } %}