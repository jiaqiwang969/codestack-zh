---
title: Data Structures in Visual Basic
caption: Data Structures
description: Articles explains the usage of data structures (types and enumerations) in Visual Basic
order: 12
---

数据结构允许将复杂的数据组作为单个类型进行存储。

例如，需要存储和修改数据条目组（例如零件编号、成本、供应商等）。在这种情况下，声明自定义结构来表示该项作为单个元素而不是使用多个变量或数组将是有益的。用户定义的类型可以在代码中声明，并且可以在此类型中添加所需的字段。此结构可以分配给变量，传递给函数或像其他值类型一样进行复制。

为了表示需要由类或函数使用的选项，可以定义枚举。枚举是一组具有自动递增的Long类型的命名常量。可以通过名称而不是值访问这些常量，因此消除了“魔法数字”的问题。

本节包含了Visual Basic代码示例，演示了不同数据结构的用法。