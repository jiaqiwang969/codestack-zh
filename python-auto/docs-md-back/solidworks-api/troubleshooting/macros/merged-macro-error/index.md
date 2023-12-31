---
layout: sw-macro-fix
title: How to fix merged SOLIDWORKS macro errors
caption: Merged Macro Does Not Work
description: Fixing Run-time error '424' - Object required for macros which work correctly independently but failed to work when merged to one
image: error-object-required.png
labels: [macro, troubleshooting]
redirect-from:
  - /2018/04/macro-troubleshooting-merged-macro-does-not-work.html
---
## 症状

SOLIDWORKS宏在独立工作时正常运行，但合并后无法工作。可能会显示错误：*运行时错误'424'：需要对象*

![运行时错误'424'：运行宏时需要对象](error-object-required.png){ width=320 height=193 }

## 原因

* 合并的宏可能不兼容
* 可能需要从源宏复制到目标宏的初始化操作未复制
* 源宏和目标宏之间的变量命名可能不同

![从记录的宏插入的代码块](zoom-to-fit-error.png){ width=320 height=221 }

## 解决方法

* 确定哪一行出错
* 检查变量的状态。将鼠标悬停在上面，查看是否在工具提示中显示为*Nothing*。
* 确保正确的宏部分被复制
* 确保所需的初始化也被复制（如果适用）
* 确保变量命名一致