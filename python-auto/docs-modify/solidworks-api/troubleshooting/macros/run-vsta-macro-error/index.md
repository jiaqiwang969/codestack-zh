---
layout: sw-macro-fix
title: Fix failed SOLIDWORKS VSTA (C# or VB.NET) macro
caption: Failed to Run VSTA (C# or VB.NET) Macro
description: Fixing the Cannot Open error when running the VSTA macro (C# or VB.NET)
image: cannot-open-vsta-macro.png
labels: [macro, troubleshooting]
redirect-from:
  - /2018/04/macro-troubleshooting-failed-to-run-vsta-macro.html
---
## 症状

无法运行SOLIDWORKS VSTA（C#或VB.NET）宏，显示*无法打开*错误。

![运行VSTA宏时显示的错误](cannot-open-vsta-macro.png){ width=320 height=129 }

## 原因

与VBA宏不同，VSTA宏是基于.NET Framework的编译内部应用程序。

主要区别在于源代码和二进制文件（交付成果）是分开的元素。

为了运行宏，需要将其编译。.NET应用程序使用互操作性与COM对象（如SOLIDWORKS）进行通信。

这意味着需要将互操作性复制到本地以运行宏。

## 解决方法

* 将输出（bin）目录中的所有文件复制为交付成果。您可以排除.pdb和.xml文件，因为这些文件用于调试和文档目的。

![编译的VSTA宏的二进制文件列表](vsta-macro-binaries.png){ width=400 height=108 }

* 如果宏没有提供这些文件，请尝试创建新的VSTA宏并复制缺少的文件。
* 如果宏（或zip归档文件）是从网络下载的，请确保文件没有被阻止，因为这可能会导致问题。

![在Windows中取消阻止dll文件的选项](unblock-dll.png){ width=217 height=320 }