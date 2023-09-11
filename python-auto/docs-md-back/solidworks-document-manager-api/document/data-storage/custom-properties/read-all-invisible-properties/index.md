---
title: Read all invisible custom properties using SOLIDWORKS Document Manager API
caption: Read All Invisible Custom Properties
description: VBA example to read and output all invisible custom properties from the specific model using SOLIDWORKS Document Manager API
labels: [invisible, custom property]
---
SOLIDWORKS模型包含多个不可见的自定义属性，例如$PRP:"SW-文件名"，$PRP:"SW-标题"。这些属性是只读的，无法修改。

这个VBA宏使用SOLIDWORKS文档管理器API从指定模型中读取和输出所有不可见的自定义属性。结果以以下格式输出到VBA编辑器的即时窗口中：

~~~
...
SW-短日期: 12/09/2019 [文本]
SW-长日期: 星期四, 12 九月 2019 [文本]
SW-配置名称: A [文本]
...
SW-创建日期: 星期二, 10 九月 2019 10:46:55 上午 [文本]
SW-上次保存日期: 星期四, 12 九月 2019 8:33:04 下午 [文本]
SW-上次保存者: artem.taturevych [文本]
...
我的属性: 我的值 [文本]
~~~

在*FILE_PATH*常量中指定要读取属性的文件。

{% code-snippet { file-name: Macro.vba } %}