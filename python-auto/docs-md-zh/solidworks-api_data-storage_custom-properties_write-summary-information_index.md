---
title: 使用SOLIDWORKS API向活动文件写入摘要信息
caption: 写入摘要信息
description: 使用SOLIDWORKS API的VBA宏，为活动的SOLIDWORKS文件填写摘要信息（作者、关键词、注释、标题、主题）
image: summary.png
labels: [摘要信息,写入摘要]
---
![SOLIDWORKS文件的摘要信息](summary.png){ width=500 }

这个VBA宏使用SOLIDWORKS API，填写活动模型的自定义属性的*摘要信息*标签（作者、关键词、注释、标题和主题）。

配置宏并指定要写入的值：

~~~ vb
Const AUTHOR As String = "CodeStack"
Const KEYWORDS As String = "sample,summary,api"
Const COMMENTS As String = "Example comments"
Const TITLE As String = "Summary API Example"
Const SUBJECT As String = "CodeStack API Examples"
~~~

{% code-snippet { file-name: Macro.vba } %}