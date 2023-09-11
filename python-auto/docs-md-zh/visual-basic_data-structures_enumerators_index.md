---
title: Visual Basic（VBA）中的枚举
caption: 枚举
description: 介绍Visual Basic中枚举数据类型（预定义的长整型常量集合）的概念
image: enum-icon-intellisense.png
---
![IntelliSense中的枚举类型](enum-icon-intellisense.png){ width=350 }

枚举是一组以[Long](visual-basic/variables/standard-types#long)类型命名的常量的结构。

与常量相比，枚举的主要优势在于能够将常量分组到单个数据类型下，并允许自动递增值。

枚举通常用于声明不同的选项或操作（例如添加、删除、移动、复制等）。

## 声明和赋值枚举

可以使用**Enum - End Enum**代码块声明枚举，每个常量在新行上声明。

~~~ vb
Enum SampleEnum_e
    Val1
    Val2
    Val3
End Enum
~~~

常量的值可以显式或隐式（自动）赋值。第一个自动值为0，并且每个下一个项目都递增1。

枚举是值类型，可以赋值给变量。可以直接使用枚举值或通过枚举名称使用。

~~~ vb
Dim enumVal As SampleEnum_e
enumVal = SampleEnum_e.Val1 '使用枚举名称
enumVal = Val1
~~~

>建议显式使用枚举名称。这样可以使代码更易读，并解决如果另一个枚举器或变量具有相同名称时可能出现的歧义。

{% code-snippet { file-name: declaration.vba } %}

## 遍历枚举值

由于枚举是长整型常量，因此可以通过知道第一个和最后一个常量来遍历所有项。

Visual Basic允许声明特殊的枚举器，这些枚举器在IntelliSense中不可见，但仍然是有效的值。为了使项目不可见，需要在名称前使用下划线_符号。例如，在枚举器的开头和结尾添加[_First]和[_Last]元素将允许定义枚举器值的边界以进行遍历。

![IntelliSense中仅显示可见的枚举器值](enum-invisible-elements.png){ width=250 }

{% code-snippet { file-name: traversing.vba } %}

## 标志枚举器（多个选项）

枚举器可以用于使用位掩码保存多个选项。

这种技术允许使用加号+符号将多个选项组合到一个变量中。可以使用**And**位运算符来判断特定选项是否已设置。

{% code-snippet { file-name: flag.vba } %}