---
title: Enumerations in Visual Basic (VBA)
caption: Enumerations
description: Introduction to enumeration data types (collection of predefined long constants) in Visual Basic
image: enum-icon-intellisense.png
---
![智能感知中的枚举类型](enum-icon-intellisense.png){ width=350 }

枚举是一组具有相同类型（Long）的命名常量的结构。

与常量相比，枚举的主要优点是能够将常量分组到单个数据类型下，并允许自动递增值。

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

常量的值可以显式或隐式（自动）赋值。第一个自动值为0，并且每个下一个项目递增1。

枚举是值类型，可以赋值给变量。可以直接使用枚举值或通过枚举名称使用。

~~~ vb
Dim enumVal As SampleEnum_e
enumVal = SampleEnum_e.Val1 '使用枚举名称
enumVal = Val1
~~~

>建议显式使用枚举的名称。这样可以使代码更易读，并解决如果另一个枚举或变量具有相同名称时可能出现的歧义。

~~~ vb
Enum MyEnum_e
    Val1 'automatically assigned value 0
    Val2 = 5 'explicitly assigned value 5
    Val3 'next automatically assigned number 6
End Enum

Enum MyIncrementEnum_e
    Val1 '0
    Val2 = Val1 + 3 '3
    Val3 = Val2 + 4 '7
End Enum

Sub main()
    
    '0 5 6
    Debug.Print MyEnum_e.Val1 & " " & MyEnum_e.Val2 & " " & MyEnum_e.Val3
    
    '0 3 7
    Debug.Print MyIncrementEnum_e.Val1 & " " & MyIncrementEnum_e.Val2 & " " & MyIncrementEnum_e.Val3
    
    'assigning the value to the variable
    Dim val As MyEnum_e
    val = MyEnum_e.Val2
    
End Sub
~~~



## 遍历枚举值

由于枚举是长整型常量，因此可以通过知道第一个和最后一个常量来遍历所有项。

Visual Basic允许声明特殊的枚举值，这些值在智能感知中不可见，但仍然是有效的值。为了使项目不可见，需要在名称前使用下划线_符号。例如，在枚举的开头和结尾添加[_First]和[_Last]元素将允许定义遍历枚举值的边界。

![智能感知中仅显示可见的枚举值](enum-invisible-elements.png){ width=250 }

~~~ vb
Enum MyFirstLastEnum_e
    [_First]
    Val1
    Val2
    Val3
    [_Last]
End Enum

Sub TraversingEnumValues()
    
    Debug.Print MyFirstLastEnum_e.[_First] '0
    Debug.Print MyFirstLastEnum_e.[_Last] '4
        
    'Traverse all enumerator values
    '1 2 3
    For enumVal = MyFirstLastEnum_e.[_First] + 1 To MyFirstLastEnum_e.[_Last] - 1
        Debug.Print enumVal
    Next
    
End Sub
~~~



## 标志枚举（多个选项）

枚举对于使用位掩码保存多个选项非常有用。

使用加号+符号可以将多个选项组合到一个变量中。可以使用**And**位运算符来确定是否设置了特定选项。

~~~ vb
Enum MyOptionEnum_e
    Option1 = 1 '2 ^ 0
    Option2 = 2 '2 ^ 1
    Option3 = 4 '2 ^ 2
    Option4 = 8 '2 ^ 3
    Option5 = 16 '2 ^ 4
End Enum

Enum MyOptionExpEnum_e
    Option1 = 2 ^ 0 '1
    Option2 = 2 ^ 1 '2
    Option3 = 2 ^ 2 '4
    Option4 = 2 ^ 3 '8
    Option5 = 2 ^ 4 '16
End Enum

Sub FlagEnums()

    Dim opts As MyOptionEnum_e
    
    '1 2 4 8 16
    Debug.Print MyOptionExpEnum_e.Option1 & " " & MyOptionExpEnum_e.Option2 & " " & MyOptionExpEnum_e.Option3 & " " & MyOptionExpEnum_e.Option4 & " " & MyOptionExpEnum_e.Option5
    
    opts = MyOptionEnum_e.Option1 + MyOptionEnum_e.Option3 + MyOptionEnum_e.Option4

    Debug.Print IsFlagSet(opts, MyOptionEnum_e.Option1)  'True
    Debug.Print IsFlagSet(opts, MyOptionEnum_e.Option2)  'False
    Debug.Print IsFlagSet(opts, MyOptionEnum_e.Option3)  'True
    Debug.Print IsFlagSet(opts, MyOptionEnum_e.Option4)  'True
    Debug.Print IsFlagSet(opts, MyOptionEnum_e.Option5)  'False
    
End Sub

Function IsFlagSet(options As MyOptionEnum_e, value As MyOptionEnum_e) As Boolean
    IsFlagSet = options And value
End Function
~~~

