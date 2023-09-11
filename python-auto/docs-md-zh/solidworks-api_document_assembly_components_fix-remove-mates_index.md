---
layout: sw-tool
title: 删除SOLIDWORKS装配体中的所有配合关系并固定组件
caption: 删除所有配合关系并固定组件
description: VBA宏，用于删除活动SOLIDWORKS装配体中的所有配合关系并固定所有顶层组件
image: remove-mates.svg
labels: [配合关系, 删除, 组件, 固定]
group: 装配体
---
![特征管理器树中的配合关系](feature-tree-mates.png)

这个VBA宏会从活动装配体中删除所有配合关系，并固定所有顶层组件。

通过更改常量的值，宏允许配置在装配体上执行的操作。

~~~ vb
Const FIX_COMPONENTS As Boolean = True 'True表示固定组件，False表示保持组件不变
Const REMOVE_MATES As Boolean = True 'True表示删除配合关系，False表示保持配合关系
~~~

> 该宏将固定所有顶层组件，但不包括模式的所有实例组件。

这样可以显著提高装配体的性能。

{% code-snippet { file-name: Macro.vba } %}