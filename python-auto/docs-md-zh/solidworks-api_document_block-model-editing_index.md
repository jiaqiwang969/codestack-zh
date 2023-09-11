---
title: 使用SOLIDWORKS API进行块模型编辑
caption: 块模型编辑
description: 该示例演示了使用SOLIDWORKS API禁用模型编辑的不同方法
labels: [块编辑, 块模型, 示例, 锁定, 菜单, solidworks api]
redirect-from:
  - /2018/03/block-model-editing.html
---

该示例演示了使用SOLIDWORKS API禁用模型编辑的不同方法：

* 阻止菜单 - 用户无法调用菜单命令。通常在显示属性管理器页面时使用此功能，以防止调用任何命令。
* 阻止模型编辑 - 模型只能查看，无法更改。
* 完全阻止 - 禁用编辑和视图操作。

需要逐步调试宏以查看不同的SOLIDWORKS API函数的实际效果。

{% code-snippet { file-name: Macro.vba } %}