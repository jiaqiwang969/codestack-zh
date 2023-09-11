---
title: 使用SOLIDWORKS API从文件中读取摘要信息
caption: 读取摘要信息
description: 使用SOLIDWORKS API的VBA宏，从活动的SOLIDWORKS文件中提取摘要信息（例如作者、关键词、注释、标题、创建信息等）
image: summary.png
labels: [摘要信息,作者,注释,标题]
---
![SOLIDWORKS文件的摘要信息](summary.png){ width=500 }

这个VBA宏使用SOLIDWORKS API从活动的SOLIDWORKS文档的自定义属性中提取数据，包括作者、关键词、注释、标题、创建信息和最后保存信息。

此宏还提取了文件创建时的SOLIDWORKS版本。

结果以以下格式输出到VBA编辑器的[即时窗口](/visual-basic/vba/vba-editor/windows#immediate-window)中：

~~~
作者：CodeStack
关键词：示例，摘要，API
注释：示例注释
标题：摘要API示例
主题：CodeStack API示例
创建时间：2019年9月10日星期二上午10:35:37
最后保存时间：2019年9月10日星期二上午11:08:23
最后保存者：artem.taturevych
最后保存工具：SOLIDWORKS 2019
创建工具：SOLIDWORKS 2012
~~~

{% code-snippet { file-name: Macro.vba } %}