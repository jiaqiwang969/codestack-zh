---
layout: sw-macro-fix
title: Fix incorrect use of 32-bit versions of Windows API functions in SOLIDWORKS macros
caption: Incorrect Use Of 32-bit Versions Of Windows API Functions
description: Fixing the Compile error - The code in this project must be updated for use on 64-bit systems when macro is utilizing Windows API functions
image: declare-function-win-api.png
labels: [macro, troubleshooting]
redirect-from:
  - /2018/04/macro-troubleshooting-incorrect-use-of-32-bit-versions-of-win-api.html
---
## 症状

系统从早于2012年的SOLIDWORKS版本升级到较新版本。
或者运行某些旧版宏。
宏使用Windows API函数（例如，具有浏览文件/文件夹对话框，连接到注册表，使用窗口句柄）通过*Declare Function*语句。
启动时显示*编译错误：必须更新此项目的代码以在64位系统上使用*。

![Windows API Declare函数不兼容错误](declare-function-win-api.png){ width=640 height=185 }

## 原因

SOLIDWORKS在2013年发布的版本中将Visual Basic for Application环境从VB6更新为VB7。
VB6是32位应用程序，而[VB7](https://msdn.microsoft.com/en-us/vba/language-reference-vba/articles/64-bit-visual-basic-for-applications-overview)是64位应用程序。
由于32位和64位环境中变量大小的差异，需要使用PtrSafe关键字来确保在x64系统中运行宏是安全的，并使用LongPtr或LongLong来正确解析32位和64位环境中的Long类型变量。

## 解决方法

* 修改所有声明并包含PtrSafe关键字和LongPtr作为Long类型的变量声明
* 如果需要支持旧版本的SOLIDWORKS（2012年之前），可以使用预编译条件语句#IF-#Else

{% code-snippet { file-name: browse-for-folder.vba } %}