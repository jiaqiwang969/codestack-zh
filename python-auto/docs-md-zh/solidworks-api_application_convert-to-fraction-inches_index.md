---
title: 使用SOLIDWORKS API将米转换为分数英寸
caption: 将米转换为分数英寸
description: 使用SOLIDWORKS API的VBA宏将系统单位（米）的值转换为分数英寸
image: dimension-fractions.png
labels: [英寸, 分数, 转换, 单位]
---
这个VBA宏将以系统单位（米）指定的值转换为具有指定分母的分数英寸。

例如，具有分母16的值0.112713将被转换为4 7/16英寸。

根据以下设置配置参数：

~~~ vb
Const DENOMINATOR As Integer = 16 '分母值
Const ROUND_TO_NEAREST_FRACTION As Boolean = True 'True表示四舍五入到最近的分数，False表示不进行四舍五入
~~~

结果和可用选项与SOLIDWORKS中的尺寸属性管理器页面相同。

![尺寸属性管理器页面中的单位覆盖选项](dimension-fractions.png)

{% code-snippet { file-name: Macro.vba } %}