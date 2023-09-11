---
layout: sw-tool
caption: 替换图纸格式
title: 在SOLIDWORKS图纸中替换图纸格式的宏
description: 根据指定的映射规则，使用VBA宏在绘图中替换图纸格式（*.slddrt文件）
image: replace-sheet-format.svg
group: 绘图
---
![图纸格式](sheet-format.png){ width=300 }

这个VBA宏根据指定的映射规则，替换活动绘图文档中所有图纸的图纸格式（*.slddrt文件）。

## 配置

通过修改**REPLACE_MAP**数组来配置映射。该数组包含了根据输入图纸的大小或图纸格式文件来替换图纸的指令。

该映射包含了一组匹配过滤器和结果图纸格式文件，格式如下：

~~~
|{源纸张大小}|{源图纸格式文件路径}|{目标图纸格式文件路径}
~~~

源纸张大小是在[swDwgPaperSizes_e](https://help.solidworks.com/2016/english/api/swconst/solidworks.interop.swconst~solidworks.interop.swconst.swdwgpapersizes_e.html)枚举中定义的常量。请参考下表。使用这些值之一，或使用\*来匹配任何纸张大小。

| 大小        | 常量 |
|-------------|----------|
| A           | 0        |
| A 纵向      | 1        |
| B           | 2        |
| C           | 3        |
| D           | 4        |
| E           | 5        |
| A4          | 6        |
| A4 纵向     | 7        |
| A3          | 8        |
| A2          | 9        |
| A1          | 10       |
| A0          | 11       |

源图纸格式文件大小是图纸格式文件的完整文件路径，或使用\*来匹配所有图纸格式。

例如，下面的映射将会：

* 无论使用哪个图纸格式文件，替换所有A0大小（11）的图纸为*D:\Formats\format1.slddrt*图纸格式。
* 无论大小如何，将所有图纸替换为与*D:\OldFormats\oldformat1.slddrt*链接的图纸格式，并使用*D:\Formats\format2.slddrt*文件。

~~~ vb
REPLACE_MAP = Array("11|*|D:\Formats\format1.slddrt", "*|D:\OldFormats\oldformat1.slddrt|D:\Formats\format2.slddrt")
~~~

您可以根据需要指定任意数量的规则。

规则按照指定的顺序执行。

如果没有规则与输入匹配-宏将抛出错误。

{% code-snippet { file-name: Macro.vba } %}