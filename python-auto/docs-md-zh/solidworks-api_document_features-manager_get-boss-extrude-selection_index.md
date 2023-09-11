---
title: 使用SOLIDWORKS API从Boss-Extrude特征中提取选择内容
caption: 从Boss-Extrude特征中提取选择内容
description: 使用SOLIDWORKS API的C# VSTA宏，从所选的Boss-Extrude特征中提取选择引用（来自实体、结束条件和方向引用）
image: boss-extrude-property-page.png
labels: [选择, Boss-Extrude]
---
这个C# VSTA宏使用SOLIDWORKS API提取Boss-Extrude特征定义中的From Entity、End Condition和Direction选择框中指定的选择实体的信息。

![Boss-Extrude特征属性管理器页面](boss-extrude-property-page.png)

提取的数据以以下格式输出到VSTA编辑器的输出窗口中。

~~~
From Entity: 是 [swSelFACES]
End Condition (Direction 1): 否
End Condition (Direction 2): 否
Direction (Direction 1): 是 [swSelSKETCHSEGS]
Direction (Direction 2): 否
~~~

{% code-snippet { file-name: Macro.cs } %}