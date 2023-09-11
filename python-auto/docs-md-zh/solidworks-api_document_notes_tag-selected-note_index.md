---
标题：使用SOLIDWORKS API为选定的注释添加标签
说明：示例演示了如何在SOLIDWORKS模型中为选定的注释添加文本标签
图片：drawing-note-revision.png
标签：[注释，标签，属性]
---
![在SOLIDWORKS图纸中带有修订号的注释](drawing-note-revision.png){ width=300 }

此示例演示了如何使用SOLIDWORKS API将文本标签（属性）添加到选定的注释中（零件、装配或图纸）。

在宏中将标签的名称指定为*TAG*常量。

* 标签允许跟踪模型会话中的特定注释。如果宏需要更新注释（例如更改修订版或链接值），这可能很有用。
* 如果注释更改其文本或格式，标签将被保留。
* 如果注释移动（包括从工作表空间移动到工作表格式），标签将被保留。
* 标签在用户界面上不可见/不可更改（只能通过SOLIDWORKS API访问）。

{% code-snippet { file-name: Macro.vba } %}