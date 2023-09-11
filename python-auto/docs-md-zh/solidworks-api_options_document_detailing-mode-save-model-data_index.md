---
caption: 切换保存时的细节模式
title: 保存SOLIDWORKS绘图时开启和关闭细节模式
description: 使用VBA宏在保存时切换细节模式的开启和关闭
---
在处理大型绘图时，使用细节模式可能会有益。为了正确使用细节模式，需要将数据保存在文档本身中。

这个过程可能会降低保存性能。

启用或禁用保存细节模式数据的切换选项由文档首选项驱动。

该宏允许打开或关闭设置并执行文档的保存。

~~~ vb
Const ENABLE As Boolean = True 'True表示保存时包含细节数据，False表示保存时不包含细节数据
~~~

可以创建两个宏按钮（一个用于保存包含细节数据，一个用于保存不包含细节数据）。

{% code-snippet { file-name: Macro.vba } %}