---
title: Standard Types in Visual Basic
caption: Standard Types
description: Overview of standard types in Visual Basic (i.e. Integer, String, Double, Object etc.) in Visual Basic
image: vba-integer-overflow.png
order: 1
---
以下分类列出了Visual Basic中不同的标准类型，按类别分组。每种类型分配不同大小的内存存储空间。一些类型具有声明字符，可以用来以简短的形式显式定义变量的类型。大多数类型提供将值从变体转换的特定函数。

## 数值类型

数值类型变量用于保存正负整数值（没有小数点），例如1、2、10、-10、-1000等。不同的数值类型允许存储不同的值范围，并且需要不同大小的分配存储空间。最常用的类型是[Integer](#integer)。

如果分配的值不适合范围，编译时将显示运行时错误'6'溢出。

![当分配的整数值超出接受范围时，显示运行时错误'6'溢出](vba-integer-overflow.png){ width=350 }

### Byte
分配1字节的存储空间。值范围从0到255。将其转换为Byte的函数是*CByte*。

### Integer
分配2字节的存储空间。值范围从-32,768到32,767。整数的类型声明字符是%。将其转换为Integer的函数是*CInt*。

### Long
分配4字节的存储空间。值范围从-2,147,483,648到2,147,486,647。长整型的类型声明字符是&。将其转换为Long的函数是*CLng*。

### LongLong
分配8字节的存储空间。值范围从-9,223,372,036,854,775,808到9,223,372,036,854,775,807。LongLong的类型声明字符是^。LongLong只是64位平台上的有效声明类型。

### LongPtr
在32位系统上表示[Long](#long)类型（4字节），在64位系统上表示[LongLong](longlong)类型（8字节）。

LongPtr通常用于编写可在32位和64位环境中运行的可移植代码。特别是在[Windows 32 API](visual-basic/windows-api)中用于指针和句柄。

## 带小数点的数值

这些类型的变量用于保存带小数点的正负数值，例如20.5、-152.89等。不同类型的变量允许存储不同范围的值，并具有不同的精度。最常用的类型是[Double](double)。对于高精度数字，可以使用[Currency](currency)或[Decimal](decimal)类型。

### Single
分配4字节的存储空间。值范围从-3.402823E38到-1.401298E–45或从1.401298E–45到3.402823E38。单精度的类型声明字符是!。将其转换为Single的函数是*CSng*。

### Double
分配8字节的存储空间。值范围从-1.79769313486232E308到-4.94065645841247E–324或从1.79769313486232E308到4.94065645841247E–324。双精度的类型声明字符是#。将其转换为Double的函数是*CDbl*。

### Currency
分配8字节的存储空间。值范围从-922,337,203,477.5808到922,337,203,685,477.5807。货币的类型声明字符是@。将其转换为Currency的函数是*CCur*。

### Decimal
分配14字节的存储空间。值范围从-79,228,162,514,264,337,593,543,950,335到79,228,162,514,264,337,593,543,950,335，或从-7.2998162514264337593543950335到7.9228162514264337593543950335。将其转换为Decimal的函数是*CDec*。请注意，Decimal类型的变量必须声明为[Variant](visual-basic/variables/standard-types#variant)，并使用*CDec*函数进行赋值。

## 逻辑类型

逻辑变量用于[条件](visual-basic/conditions)中，表示为1（True）或0（False）。

### Boolean
分配2字节的存储空间。可以是True或False。将其转换为Boolean的函数是*CBool*。

## 文本类型

文本变量用于保存文字，定义时用双引号""括起来。

### String
分配10个字节加上字符数的存储空间。值范围从0到20亿个字符。将其转换为String的函数是*CStr*。

## 日期和时间类型

保存日期和时间信息的变量。

### Date
分配8字节的存储空间。值范围从公元100年1月1日到公元9999年12月31日。将其转换为String的函数是*CDate*。

## 引用类型

这些变量是任何可能保存复杂数据和结构的引用类型。

### Object
分配4字节的存储空间。用于[后期绑定](visual-basic/variables/declaration#early-binding-and-late- binding)

## 任意类型

这些变量类型可以保存任何数据对象（值类型、引用类型或数组）

### Variant
分配16字节的存储空间。将其转换为Variant的函数是*CVar*。

下面的代码示例演示了各种标准数据类型的声明和转换。

~~~ vb
Sub main()
    
    Dim byteVar As Byte
    byteVar = 17
    byteVar = CByte("12") 'converting from text value to byte
    byteVar = CByte(15.6) 'floating number is not acceptable so the value will be rounded to 16
    
    Dim intVar As Integer
    intVar = 12567
    intVar = CInt("124")
    
    Dim longVar As Long
    longVar = 1256936
    longVar = CLng("-124")
    longVar = 123&
    
    Dim longLongVar As LongLong '64 bit only
    longLongVar = 103456
    longLongVar = 7392984646^
    
    Dim longPtrVar As LongPtr
    longPtrVar = 94874882
    
    Dim singleVar As Single
    singleVar = 3.4E+38 '3.4 * 10^38
    singleVar = CSng("15.656")
    singleVar = 12345.35!
    
    Dim doubleVar As Double
    doubleVar = 3.4E+100
    doubleVar = CDbl("106.278856") 'holds more precise value with more floating digits
    doubleVar = 12345# 'force integer value to be converted to double
    
    Dim currVal As Currency
    currVal = 3105.6
    currVal = CCur("31,256,78")
    currVal = 689.3458@
    
    Dim decVal As Variant
    decVal = CDec(1E-18)
    
    Dim boolVar As Boolean
    boolVar = True
    boolVar = CBool(1) 'converted to true
    
    Dim strVar As String
    strVar = "Hello World"
    strVar = CStr(125) 'number converted to string
    
    Dim dateVar As Date
    dateVar = Now() 'assigns current date
    dateVar = CDate("10-Jun-2018")
    
    Dim objVar As Object
    Set objVar = Nothing
    
    Dim varVar As Variant
    varVar = Array("A", "B", "C")
    varVar = "Hello World"
    varVar = CVar(10.5)
    
End Sub

~~~


