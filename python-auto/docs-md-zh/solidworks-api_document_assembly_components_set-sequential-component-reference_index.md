---
caption: 设置顺序组件引用
title: 宏以自动按顺序分配SOLIDWORKS组件引用
description: VBA宏以基于种子数自动递增和分配所选组件的顺序引用
image: component-reference.png
---
![组件引用](component-reference.png){ width=600 }

该VBA宏允许自动为SOLIDWORKS装配中的所选组件引用分配数字编号

编号根据指定的种子值自动递增

编号按照组件在装配中被选择的顺序进行分配

组件可以在特征管理器树或图形区域中选择（可以选择组件的任何实体，例如面或边）

宏可以配置为在弹出框中指定输入（将**INPUT_SEED**变量的值设置为**True**），或者通过提供种子作为常量来指定输入（**INPUT_SEED**等于**False**且**SEED**等于种子数）

~~~ vb
Const INPUT_SEED As Boolean = True '在运行宏时在输入框中输入种子（起始）数
Const SEED As Integer = 1
~~~

{% code-snippet { file-name: Macro.vba } %}