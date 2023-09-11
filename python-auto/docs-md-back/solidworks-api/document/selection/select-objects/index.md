---
title: Select any SOLIDWORKS objects in a batch using API
caption: Select Any Objects In A Batch
description: Example demonstrates how to select any SOLIDWORKS objects (entities, features, annotations, etc.) in a batch mode
image: select-objects.png
labels: [selection, batch selection, dispatch]
---
![在图形区域中选择不同类型的对象](select-objects.png)

本示例演示了如何以批量模式选择任意SOLIDWORKS对象（实体、特征、注释等）。

当事先不知道对象类型时，这种技术非常有用。与使用SOLIDWORKS API逐个选择对象相比，一次选择多个对象可以提高性能。

以下示例提供了类似于SOLIDWORKS的[创建选择集](https://help.solidworks.com/2015/english/whatsnew/t_creating_selection_sets.htm)的功能。

![创建选择集上下文菜单命令](create-selection-set.png){ width=300 }

* 打开任何模型并选择任意对象（可以是不同类型的对象，如特征、实体、注释等）
* 运行宏。宏将收集所有选定对象的指针
* 清除选择并停止执行宏
* 继续执行，之前选定的所有对象将被重新选择。

<details open>
<summary>VBA示例</summary>
{% code-snippet { file-name: Macro.vba } %}
</details>

<details open>
<summary>C#示例</summary>
{% code-snippet { file-name: vsta-macro.cs } %}
</details>