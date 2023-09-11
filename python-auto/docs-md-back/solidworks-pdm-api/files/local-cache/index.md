---
title: Cache file from PDM vault locally using SOLIDWORKS PDM API
caption: Cache File Locally
description: Example demonstrates how to get local copies of the file and all the dependencies using PDM Professional API to be used in desktop application
image: get-latest-version.png
labels: [local copies]
---
本示例演示了如何获取文件及其所有依赖项的本地副本，以供桌面应用程序使用。此宏相当于以下命令：

![在PDM保险库中获取最新版本命令](get-latest-version.png){ width=350 }

PDM是一种基于服务器的应用程序，当通过Windows文件资源管理器在PDM中访问文件时，文件会被缓存在本地。文件缓存可能会被清除或过时。这意味着如果文件在PDM保险库中没有被本地缓存，桌面应用程序在尝试访问该文件时可能会失败。将会出现文件未找到的错误（例如，使用SOLIDWORKS API打开文件或使用文件系统对象遍历文件夹结构或读取任何属性）。

为了提高性能，此宏利用了[SOLIDWORKS PDM API接口](https://help.solidworks.com/2018/english/api/epdmapi/epdm.interop.epdm~epdm.interop.epdm.iedmbatchget.html)中的[IEdmBatchGet](https://help.solidworks.com/2018/english/api/epdmapi/epdm.interop.epdm~epdm.interop.epdm.iedmbatchget.html)接口，该接口可以批量处理文件。

要测试此场景：

* 获取保险库中任何SOLIDWORKS文件的路径
* 清除保险库的缓存：

![清除本地缓存命令](clear-local-cache.png){ width=450 }

* 在以下宏的*main*过程中注释掉*GetLocalCopyFromVault*调用
* 运行宏。注意到*swModel*的指针为空，文件打开调用失败
* 取消注释*GetLocalCopyFromVault*并再次运行宏。现在模型成功打开，因为文件已在本地缓存中。


{% code-snippet { file-name: Macro.vba } %}