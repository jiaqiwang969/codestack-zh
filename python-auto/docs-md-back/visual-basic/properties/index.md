---
caption: Properties
title: Properties in Visual Basic
description: Article explaining usage (declaring, setting and reading the values) of properties in Visual Basic. Difference between properties and variables
order: 14
---
属性在使用上与[变量](/visual-basic/variables/declaration/)非常相似，当涉及到属性的使用时。

~~~ vb jagged
Set myObj = Property1 '将属性的引用值分配给变量
myInt = Property2 '将属性的整数值分配给变量
Property3 = 0.1 '将双精度值分配给属性
Set Property4 = CreateObject("ComClass") '将 COM 类的实例分配给属性
~~~

如果 Property1、Property2、Property3 和 Property4 被声明为变量，上述代码将完全相同，并且在使用上没有区别。它们也将具有相同的智能感知图标。

![属性和变量的智能感知](property-intellisense.png)

然而，属性的声明更类似于[函数](/visual-basic/functions/)。

## 属性的类型

有三种类型的属性：

### 只读属性

这些属性只能返回值。这些属性的行为类似于函数：

{% code-snippet { file-name: Macro.vba, regions: [ read-only ] } %}

尝试将值分配给只读属性会导致*无效限定符*的编译错误。

![尝试将值分配给只读属性时的无效限定符错误](invalid-qualifier-error.png)

### 只写属性

与只读属性相反，只写属性用于分配值。这些属性的行为类似于子过程。

{% code-snippet { file-name: Macro.vba, regions: [ write-only ] } %}

有 *Let* 和 *Set* 两种写属性。*Let* 应该用于简单类型，如 *String*、*Integer*、*Double*，而 *Set* 属性应该用于引用类型，如 *Object* 或自定义类的实例。

> 注意，仍然可以将 Let 属性用于引用类型，但在这种情况下，不需要使用 Set 关键字将值分配给属性。然而，这不是推荐的做法，因为这会使代码变得不太可读，并且与函数和变量不一致，其中 Set 关键字始终与引用类型一起使用。

### 读写属性

读写属性是在单个属性中结合了读取和写入功能。

{% code-snippet { file-name: Macro.vba, regions: [ read-write ] } %}

读写属性的声明必须具有相同的名称和相同的类型，即写属性中的参数类型必须与读属性中的返回值类型相匹配，否则将抛出*属性过程的定义不一致，或属性过程具有可选参数、ParamArray 或无效的 Set 最终参数*的编译时错误。

{% code-snippet { file-name: MacroError.vba } %}

![不一致的属性错误](inconsistent-property-error.png)

请注意，当未显式声明属性的类型时，它将被视为 Variant 类型。

## 带参数的属性

虽然很少使用，但属性可以具有额外的参数。

{% code-snippet { file-name: Macro.vba, regions: [ parameters ] } %}

> 如果属性需要多个参数，请考虑使用函数。

## 使用方法

尽管属性可以被认为是多余的，因为属性所涵盖的所有功能都可以通过函数实现，但属性提供了更好的代码可读性和更容易使用类或模块。建议将属性用于描述实体属性而不是动作的元素，例如对于类 *Car*，将 *Color*、*Made*、*YearOfManufacturing* 声明为属性（而不是 *GetColor*、*SetColor*、*GetMade* 等函数），而 *Drive* 应该声明为过程。