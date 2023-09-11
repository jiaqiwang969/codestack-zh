---
caption: 将随机颜色应用于组件
title: 在SOLIDWORKS装配中应用随机颜色的宏
description: VBA宏，将随机颜色应用于SOLIDWORKS装配中的所有组件，并可按自定义属性值进行分组。
---
这个VBA宏将在活动装配中的所有组件上应用随机颜色。

修改宏的常量以更改颜色的级别（组件级别或模型级别）。

如果将颜色应用于各个配置（例如**ALL_CONFIGS** = **False**），文档必须有与配置关联的显示状态，否则颜色不能是配置特定的。

~~~ vb
Const COMP_LEVEL As Boolean = True 'True表示在装配级别应用颜色，False表示在模型级别应用颜色
Const PARTS_ONLY As Boolean = True 'True表示仅处理零件组件，False表示也将颜色应用于装配
Const ALL_CONFIGS As Boolean = True 'True表示将颜色应用于所有配置，False表示仅应用于引用的配置
~~~

~~~ vb
Const PRP_NAME As String = "Type" '按此自定义属性对组件进行分组的自定义属性，空字符串 "" 表示不分组组件

Sub InitColors(Optional dummy As Variant = Empty)

    ColorsMap.Add "Plate", RGB(255, 0, 0) '将所有自定义属性'Type'等于'Plate'的组件颜色设置为红色
    ColorsMap.Add "Beam", RGB(0, 255, 0) '将所有自定义属性'Type'等于'Beam'的组件颜色设置为绿色
    
End Sub
~~~

{% code-snippet { file-name: Macro.vba } %}