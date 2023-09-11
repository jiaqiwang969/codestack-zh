---
title: Comments in Visual Basic
caption: Comments
description: Article explaining the usage of comments to annotate the code
order: 8
---
注释是可以放在代码中进行注解和参考的自由文本。编译器会忽略注释，并允许在其中添加任何文本。

在 Visual Basic 中，注释是指放在撇号 **'** 符号和行尾之后的任何文本。尽管颜色方案是可调整的，但在 Visual Basic 中注释的默认颜色是绿色。

注释可以添加在行的开头：

~~~ vb
'函数正在执行一些代码
Sub DoWork()
End Sub
~~~

注释也可以放在行的末尾：

~~~ vb
Dim a As String '声明字符串变量
a = "Hello World" '给字符串变量赋值
~~~

尽管注释是注解代码的好工具，但请尽量不要过多地使用注释，因为这可能会使代码看起来很繁忙。相反，尽量使用描述性的变量名和函数名。

> 好的代码自解释

不要这样写：

~~~ vb
Dim var1 As String
var1 = = "Xarial" '公司名称
~~~

而要这样写：

~~~ vb
Dim companyName As String
companyName = "Xarial"
~~~

还要避免为显而易见的代码添加注释。例如，下面的代码中的注释是重言式，不应该添加：

~~~ vb
'计算值的平方根
Function CalculateSquareRoot(val as double)
End Function
~~~

一般来说，我建议在以下情况下添加注释：

* 教育和教程目的
* 对于不容易理解的代码，可能是一些复杂的算法
* 对于解决方法，即某个功能可以用更简单的方式完成，但已知存在限制或错误。例如，在使用第三方 API 时可能会出现问题的方法
* 作为未来工作的占位符。在这种情况下，您可以使用 **TODO** 占位符

~~~ vb
Function IsValid() As Boolean
    'TODO: 实现验证
    IsValid = True
End Function
~~~