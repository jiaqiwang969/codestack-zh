---
layout: sw-tool
title: Macro feature to increment the numeric value in the note via SOLIDWORKS API
caption: Increment The Numeric Value In The Note
description: This macro increments the numeric value of the notes by matching regular expression (e.g. incrementing the revision) using SOLIDWORKS API
image: drawing-revision-incremented.png
labels: [note, revision, increment, regular expression, regex, tag]
group: Drawing
---
![标题块中的修订号已增加](drawing-revision-incremented.png){ width=300 }

该宏使用SOLIDWORKS API来增加注释的数值。如果需要增加注释的修订版本而无需手动选择和更改注释，则这将非常有用。该宏还可以在批处理软件中使用。

![通过运行宏按钮中的宏来增加标题块中的修订号](increment-revision-macro.gif)

* 数值通过指定的[正则表达式](https://en.wikipedia.org/wiki/Regular_expression)进行匹配。可以修改正则表达式以匹配特定的数值。注释可以包含自由文本（在这种情况下，只有数值部分将根据指定的正则表达式进行更新）
* 需要在注释中添加文本标签以增加其数值。请按照[向选定的注释添加标签](/solidworks-api/document/notes/tag-selected-note)示例中的说明添加标签到注释中。
* 默认情况下，数值将增加1，但可以通过修改*IncrementNoteValue*函数的*increment*参数的值来更改。

{% code-snippet { file-name: Macro.vba } %}