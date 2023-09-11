---
layout: sw-tool
title: 用于给SOLIDWORKS钣金和焊接零件切割清单着色的宏
caption: 着色切割清单
description: SOLIDWORKS VBA宏，根据自定义属性的值为所有切割清单项（钣金和焊接零件）着色
image: color-cut-list.svg
labels: [切割清单,钣金,焊接,着色]
group: 切割清单
---
这个VBA宏允许根据自定义属性的值为每个切割清单项（钣金或焊接零件）分配一个独特的颜色。

这个宏最常见的用途是根据型材尺寸区分不同类型的焊接零件。

宏将自动为特定的组分配随机颜色。也可以指定特定组使用的固定颜色。

## 配置

为了指定从中读取值并对切割清单项进行分组的自定义属性的名称，请更改**PRP_NAME**常量的值

~~~ vb
Const PRP_NAME As String = "Description" '将Description的值更改为选择不同的自定义属性
~~~

为了指定颜色，需要修改**InitColors**方法中的值。

~~~ vb
Sub InitColors(Optional dummy As Variant = Empty)

    ColorsMap.Add "SB BEAM 80 X 6", RGB(255, 0, 0)
    ColorsMap.Add "TUBE, RECTANGULAR 50 X 30 X 2.60", RGB(0, 255, 0)
    
End Sub
~~~

要向映射中添加新颜色，请添加以下行

~~~ vb
ColorsMap.Add "[属性值]", RGB([红色], [绿色], [蓝色])
~~~

例如，要将蓝色（RGB = 0, 0, 255）添加到焊接型材"50 X 50"，需要添加以下行

~~~ vb
ColorsMap.Add "50 X 50", RGB(0, 0, 255)
~~~

{% code-snippet { file-name: Macro.vba } %}