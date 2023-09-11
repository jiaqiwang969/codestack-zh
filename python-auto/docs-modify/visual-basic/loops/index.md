循环是编程中一种迭代遍历集合、数组和其他数据集的技术。

以下部分介绍了不同类型的循环。以下所有示例都基于下面声明的一个简单的*String*数组：

{% code-snippet { file-name: Macro.vba, regions: [init] } %}

然而，类似的技术可以用于任何类型的数组。

## For-Next

这可能是最常见的循环类型。它允许执行指定次数的迭代。默认情况下，每次循环迭代都会将索引值增加一。

{% code-snippet { file-name: Macro.vba, regions: [for] } %}

上面的示例将打印数组中的所有值：

> A B C D E F G H I J

或者，可以使用*Step*关键字指定不同的步长值。步长可以为负数以逆向迭代。

{% code-snippet { file-name: Macro.vba, regions: [for-reverse] } %}

上面的代码将以逆向顺序输出值：

> J I H G F E D C B A

## While-Wend

此循环在条件为*True*时执行。

当迭代次数事先不知道时，这种类型的循环很有用。

{% code-snippet { file-name: Macro.vba, regions: [while] } %}

上面的代码将输出并在当前元素等于*D*时终止：

> A B C D

## Do-Loop While

**Do-Loop While**与**While-Wend**循环类似，但条件在执行步骤之后执行，因此它确保至少执行一次迭代，无论条件如何。

{% code-snippet { file-name: Macro.vba, regions: [do] } %}

上面的代码将产生以下结果：

> A B C D

## For Each-Next

尽管在大多数情况下，**For-Next**循环用于迭代数组的元素，但它不仅限于此用例。循环体中可以执行任何代码。

要专门迭代数组的元素，可以使用**For Each-Next**循环。

{% code-snippet { file-name: Macro.vba, regions: [foreach] } %}

上面的代码片段将输出：

> J I H G F E D C B A

## 无限循环

循环条件的错误使用可能导致无限循环。这种代码通常导致软件挂起或崩溃。

例如，下面的循环将无限运行，因为**i**变量从未递增。

{% code-snippet { file-name: Macro.vba, regions: [infinite] } %}

要终止无限循环（或在VBA中停止任何正在运行的代码），可以按下组合键：*ctrl+alt+pause/break*

这将显示下面的消息框，可以停止代码或进入调试模式。

![终止无限循环](terminate-code-execution.png)