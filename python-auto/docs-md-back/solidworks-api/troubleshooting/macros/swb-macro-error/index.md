---
layout: sw-macro-fix
title: Fixing the error when running legacy SWBasic (*.swb) SOLIDWORKS macro
caption: SWBasic (*.swb) macro error
description: Fixing the error when running or editing the legacy macro in swb format
image: swbasic-swb-macro-filter.png
labels: [macro, troubleshooting]
---
## 症状

![选择 SWBasic 宏 (*.swb)](swbasic-swb-macro-filter.png)

在编辑时，以 *.swb 格式存储的传统 SOLIDWORKS 宏会出现“编译错误：未定义的用户类型”错误。如果从“工具->宏->运行”菜单中运行，通常可以正常运行：

![编译错误：未定义的用户类型](swb-macro-user-defined-type-not-defined-error.png){ width=300 }

## 原因

SWBasic 宏是以 ASCII 格式（即纯文本）存储的脚本，无法存储任何引用信息。SOLIDWORKS 类型是在 SOLIDWORKS 类型库中定义的，这些类型库在 SWBasic 宏中默认没有引用。

## 解决方法

* 打开要编辑的宏（工具->宏->编辑）
* 导航到 *工具->引用* 菜单

![VBA 编辑器中的引用菜单](vba-tools-references.png){ width=300 }

* 检查所有 SOLIDWORKS 类型库

![VBA 引用对话框中的 SOLIDWORKS 类型库](vba-sw-references.png){ width=300 }

* 以 *.swp 格式保存宏