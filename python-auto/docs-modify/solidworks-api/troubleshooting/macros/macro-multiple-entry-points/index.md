---
layout: sw-macro-fix
title: Failed to run SOLIDWORKS macro with multiple entry points
caption: Multiple Entry Points In The Macro
description: Fixing the macro which doesn't work if it is run from the Tools->Macro->Run menu in SOLIDWORKS but works correctly if opened in the VBA editor and executed via F5 or by clicking green arrow
image: error-object-variable-or-with-block-variable-not-set.png
labels: [macro, troubleshooting]
redirect-from:
  - /2018/04/macro-troubleshooting-multiple-entry-points-in-macro.html
---
## 症状

如果从SOLIDWORKS的工具->宏->运行菜单中运行SOLIDWORKS宏，则宏无法正常工作。

这可能会产生类似于“运行时错误'91'：对象变量或With块变量未设置”的错误。

!['运行时错误'91'：运行宏时出现对象变量或With块变量未设置的错误](error-object-variable-or-with-block-variable-not-set.png){ width=320 height=194 }

或者宏可能会表现异常，或者根本不执行任何步骤。
如果在VBA编辑器中打开并通过F5或点击绿色箭头（运行）按钮执行，宏将正常运行。

## 原因

当宏启动时，SOLIDWORKS会尝试找到入口点（要首先执行的子程序（sub））。这将是不包含任何参数的sub。

如果宏包含多个这样的sub，则会产生歧义，任何sub都可以成为入口点。

{% code-snippet { file-name: get-features-count.vba } %}

入口sub非常关键，因为它通常包含初始化程序，如果不按正确顺序执行，则宏逻辑将受到影响。

## 解决方法

* 始终保留一个无参数的子程序（通常称为main）。对于不需要输入参数的其他sub，如果必要，可以使用*dummy*参数来防止不正确的行为。可以为该参数传递任何值，因为它不会被使用（例如""或Empty）。

~~~ vb
Call AnotherProc(Empty) '调用带有空值的sub
----
Sub AnotherProc(dummy) '未使用的dummy参数
End Sub
~~~

{% code-snippet { file-name: get-features-count-fix.vba } %}

* [将宏分配给按钮](/solidworks-api/getting-started/macros/macro-buttons)。在这种情况下，将需要强制选择入口点sub，以防止宏中存在多个无参数sub时产生歧义。