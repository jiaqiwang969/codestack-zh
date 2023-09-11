---
caption: 将绘图导出为PDF文件到选定文件夹
title: 宏以将活动绘图保存为PDF文件到选定的输出文件夹并关闭绘图
description: 这是一个VBA宏，可以执行以下操作：

* 显示“浏览文件夹”对话框，选择PDF文件的输出文件夹
* 将活动绘图保存为PDF文件，保存到上一步选择的文件夹中。PDF文件的文件名与绘图的文件名相同
* 如果原始绘图已被修改，宏会保存更改
* 关闭活动的SOLIDWORKS绘图文档

{% code-snippet { file-name: Macro.vba } %}