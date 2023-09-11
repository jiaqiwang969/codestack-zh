---
layout: sw-tool
title: 删除SOLIDWORKS装配体中的所有约束和固定零件
caption: 删除所有约束和固定零件
description: VBA宏，用于删除活动SOLIDWORKS装配体中的所有约束并固定所有顶层零件
image: remove-mates.svg
labels: [约束, 删除, 零件, 固定]
group: 装配体
---
![特征管理器树中的约束](feature-tree-mates.png)

此VBA宏从活动装配体中删除所有约束并固定所有顶层零件。

通过更改常量的值，宏允许配置在装配体上执行的操作

~~~ vb
Const FIX_COMPONENTS As Boolean = True 'True表示固定零件，False表示保持零件不变
Const REMOVE_MATES As Boolean = True 'True表示删除约束，False表示保持约束
~~~

> 该宏将固定所有顶层零件，但不包括模式的所有实例零件

这样可以显著提高装配体的性能。

{% code-snippet { file-name: Macro.vba } %}