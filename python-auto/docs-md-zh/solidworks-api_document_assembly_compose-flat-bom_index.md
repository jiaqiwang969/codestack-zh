---
title: 使用SOLIDWORKS API编写VBA宏来生成平面BOM表
caption: 生成平面物料清单（BOM）
description: 本示例演示了如何使用SOLIDWORKS API从装配树中生成物料清单（BOM）
image: bill-of-materials.png
labels: [BOM, 平面, 顶层]
---
![物料清单](bill-of-materials.png){ width=250 }

本示例演示了如何使用SOLIDWORKS API从装配树中生成平面（仅顶层）物料清单表。

物料清单的位置包括以下列：

* 模型路径
* 模型配置
* 描述（自定义属性）
* 价格（自定义属性）
* 数量（计算得出）

生成的BOM将输出到VBA编辑器的即时窗口中：

![在即时窗口中打印的BOM表](flat-bom-print.png){ width=250 }

不需要插入BOM表格即可运行此宏。

{% code-snippet { file-name: Macro.vba } %}