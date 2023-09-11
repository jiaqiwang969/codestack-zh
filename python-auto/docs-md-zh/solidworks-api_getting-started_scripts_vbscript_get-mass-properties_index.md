---
title: 使用SOLIDWORKS API提取文件的质量属性的脚本示例
caption: 获取质量属性
description: 该示例演示了如何使用vbScript和SOLIDWORKS API从指定的文件中提取质量属性。
image: msgbox-mass-properties.png
labels: [质量属性, vbScript]
---

该示例演示了如何使用vbScript通过SOLIDWORKS API从指定的文件中提取质量属性。

* 创建一个文本文件，并将其命名为*get-mass-prps.vbs*
* 将以下代码复制粘贴到文件中

{% code-snippet { file-name: script.vbs } %}

* 保存文件
* 双击运行脚本
* 在显示的输入框中指定SOLIDWORKS文件（零件或装配）的完整路径
* 结果将在消息框中显示以下质量属性值

![指定模型的质量属性显示在消息框中](msgbox-mass-properties.png){ width=250 }