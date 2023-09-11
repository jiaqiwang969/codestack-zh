---
title: 在Visual Basic中使用递归技术
caption: 递归
description: 解释递归并在Visual Basic中使用它来输出物料清单（BOM）的结构。
---
在某些情况下，可能需要解析分层数据。这是一种树形结构的数据，其中包含一组节点，每个节点可能包含子节点的集合，每个子节点又可以有自己的子节点集合，依此类推。分层数据的示例是包含可能具有子节点的节点的XML文件。

可以使用[循环](/visual-basic/loops/)来解析这些数据，但这个任务会变得复杂，并且代码的可读性会受到影响。更简单的解决方案是使用递归技术。

这个函数将解析单个节点（或单个层级上的节点），然后递归调用自身来处理所有子节点。

例如，以下物料清单（BOM）结构表示一个产品。

![BOM结构示例](bom.svg){ width=350 }

在Visual Basic中，可以使用以下类来描述这个结构，其中**Children**变量可能包含子装配节点的子节点。

## BomItem类

{% code-snippet { file-name: BomItem.vba } %}

为了输出结构，可以编写以下函数

{% code-snippet { file-name: Macro.vba, regions: [recursion] } %}

作为结果，以下信息将输出到VBA编辑器的即时窗口。

~~~
A (1)
-B (2)
--D (1)
--E (5)
--F (1)
-C (3)
~~~