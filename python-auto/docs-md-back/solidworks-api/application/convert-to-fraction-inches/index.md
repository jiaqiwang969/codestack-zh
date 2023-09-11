---
title: Convert meters to fraction inches using SOLIDWORKS API
caption: Convert Meters To Fraction Inches
description: VBA macro to convert value in system units (meters) to the fraction inches using SOLIDWORKS API
image: dimension-fractions.png
labels: [inches,fraction,conversion,unit]
---
这个VBA宏将以系统单位（米）指定的值转换为指定分母的分数英寸。

例如，带有分母16的值0.112713将被转换为4 7/16英寸。

根据以下设置配置参数：

~~~ vb
Const DENOMINATOR As Integer = 16 '分母值
Const ROUND_TO_NEAREST_FRACTION As Boolean = True 'True为四舍五入到最近的分数，False为不进行四舍五入
~~~

结果和可用选项与SOLIDWORKS中的尺寸属性管理器页面相同。

![尺寸属性管理器页面中的单位覆盖选项](dimension-fractions.png)

{% code-snippet { file-name: Macro.vba } %}