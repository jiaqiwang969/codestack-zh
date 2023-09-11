---
title: 使用eDrawings标记API捕获SOLIDWORKS实体的测量
caption: 捕获测量
description: 使用eDrawings标记API将SOLIDWORKS模型中的实体测量捕获到文本框中
image: surveying-form.png
labels: [edrawings,标记,测量]
---
![测量结果显示在文本框中](surveying-form.png){ width=450 }

本示例演示了如何使用eDrawings标记API将所选实体的测量结果捕获到文本框中。

本示例基于[在Windows Forms中托管eDrawings控件](/edrawings-api/gettings-started/winforms/)

* 运行表单
* 通过指定文件的完整路径并点击“打开”按钮来打开任何SOLIDWORKS或eDrawings文件
* 测量功能会自动启用
* 选择任意实体并点击“捕获测量”。测量值将追加到文本框中

{% code-snippet { file-name: MainForm.cs } %}

源代码可在[GitHub](https://github.com/codestackdev/solidworks-api-examples/tree/master/edrawings-api/MeasurementSurveying)上找到。