---
title: Script extract mass properties of file using SOLIDWORKS API
caption: Get Mass Properties
description: Example demonstrates how to extract mass properties form the specified file using vbScript and SOLIDWORKS API
image: msgbox-mass-properties.png
labels: [mass properties, vbscript]
---

该示例演示了如何使用vbScript通过SOLIDWORKS API从指定的文件中提取质量属性。

* 创建一个文本文件，命名为*get-mass-prps.vbs*
* 将以下代码复制粘贴到文件中

{% code-snippet { file-name: script.vbs } %}

* 保存文件
* 双击运行脚本
* 在显示的输入框中指定SOLIDWORKS文件（零件或装配）的完整路径
* 结果将在消息框中显示以下质量属性值

![指定模型的质量属性显示在消息框中](msgbox-mass-properties.png){ width=250 }