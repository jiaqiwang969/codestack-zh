---
title: Visual Basic 中的用户定义类型
caption: 类型
description: 解释在 Visual Basic 中使用自定义用户定义类型（也称为结构）的文章
image: type-definition-intellisense.png
---
![智能感知中的用户定义类型](type-definition-intellisense.png){ width=350 }

在 Visual Basic 中，可以使用 **Type - End Type** 代码块定义复杂的数据结构（组）变量。

~~~ vb
Type MyType
    Var1 As Double
    Var2 As String
End Type
~~~

这使开发人员能够创建易于理解和使用的数据结构。

可以在类型代码块中定义任何类型的变量。

在类型中声明的属性是公共的，并且可以在智能感知中浏览：

![在智能感知中显示的用户定义类型的属性](type-properties-intellisense.png){ width=250 }

无法在类型中设置访问修饰符或添加任何函数或过程：

![编译错误：Type 块内的语句无效](statement-invalid-type-block.png){ width=350 }

{% code-snippet { file-name: declaration-usage.vba } %}