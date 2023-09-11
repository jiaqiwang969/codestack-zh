---
layout: sw-tool
title: 宏功能：在重建时自动运行SOLIDWORKS宏
caption: 在重建时自动运行宏
description: 通过宏功能和SOLIDWORKS API设计的绑定附件，允许在每次重建时自动运行宏
image: design-binder-macro-attachment.png
labels: [自动运行, 宏, 重建]
group: 模型
redirect-from:
  - /solidworks-api/document/run-macro-on-rebuild/
---
此宏允许使用SOLIDWORKS API在每次重建操作时自动运行指定的宏。

设置宏的步骤如下：

* 运行宏
* 指定要运行的宏的完整路径
![选择要运行的宏的路径](input-macro-file-path.png){ width=250 }

此宏将作为设计绑定附件添加到模型中
![宏作为设计绑定附件添加](design-binder-macro-attachment.png){ width=250 }
* 宏功能将作为树中的最后一个特征插入宏中。

当模型重建时（手动或自动），宏将自动运行。

默认情况下，宏功能和宏被嵌入到模型中。这意味着可以在没有此宏的任何其他工作站上打开并更新模型。

这也可以直接嵌入到文档模板中。

### 选项
可以通过常量更改宏功能的名称

~~~ vb
Const BASE_NAME As String = "[特征名称]"
~~~

默认情况下，宏被嵌入到模型中。为了编辑宏代码，请使用设计绑定附件中的“编辑”命令

![在设计绑定中编辑嵌入的宏](edit-embeded-macro.png){ width=250 }

为了避免嵌入宏，请将以下常量更改为*False*

~~~ vb
Const EMBED_MACRO As Boolean = False
~~~

{% code-snippet { file-name: Macro.vba } %}