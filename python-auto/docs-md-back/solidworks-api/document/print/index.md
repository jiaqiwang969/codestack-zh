---
layout: sw-tool
caption: Print
title: Macro to print SOLIDWORKS documents
description: VBA macro to print SOLIDWORKS documents using the specified settings (printer name, printer range, orientation, paper size and scale)
image: printer.svg
group: Model
---
![打印机和页面设置](page-setup.png){ width=500 }

这个VBA宏允许打印当前的SOLIDWORKS文档。可以指定打印的设置：打印机名称、打印范围、方向、纸张大小和比例。

## 设置

要配置设置，请根据下面的说明更改宏顶部的常量值。

~~~ vb
Const PRINTER_NAME As String = "Microsoft Print To PDF" '打印机的完整名称
Const PRINT_RANGE As String = "1-3,5" '要打印的范围。使用*打印所有页面或指定范围
Const PRINT_ORIENTATION As Integer = swPageSetupOrientation_e.swPageSetupOrient_Landscape '方向：横向或纵向
Const PRINTER_PAPER_SIZE As String = "A3" '要打印的纸张大小
Const PRINT_SCALE As String = "*" '打印比例。使用*自适应比例或指定比例的值（1到1000的百分比）
~~~

{% code-snippet { file-name: Macro.vba } %}