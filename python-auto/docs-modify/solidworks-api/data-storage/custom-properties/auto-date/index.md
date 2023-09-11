---
layout: sw-tool
caption: Auto Date Custom Property
title: Create a dynamic auto updatable date custom property in SOLIDWORKS file
description: VBA macro which creates a date custom property in SOLIDWORKS file in the specified format with an option to automatically update
image: auto-date-custom-property.svg
group: Custom Properties
---

这个VBA宏允许将自定义属性**日期**插入到文件特定的自定义属性中。用户可以指定日期的格式。请参考[日期和时间格式字符串](https://docs.microsoft.com/zh-cn/dotnet/standard/base-types/standard-date-and-time-format-strings)以获取更多关于支持的格式的信息。

## CAD+

这个宏与[Toolbar+](https://cadplus.xarial.com/toolbar/)和[Batch+](https://cadplus.xarial.com/batch/)工具兼容，因此可以将按钮添加到工具栏并分配快捷键以便更方便地访问或批量运行。

要启用[宏参数](https://cadplus.xarial.com/toolbar/configuration/arguments/)，请将**ARGS**常量设置为true，并将格式作为参数传递。

~~~ vb
#Const ARGS = True
~~~

{% code-snippet { file-name: Macro.vba } %}

这个宏还可以嵌入到模型中，以便在每次重建时自动更新日期。

{% code-snippet { file-name: MacroFeature.vba } %}