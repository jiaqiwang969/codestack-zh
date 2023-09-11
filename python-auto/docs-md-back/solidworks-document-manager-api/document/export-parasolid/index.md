---
layout: sw-tool
title: Export part to Parasolid via Document Manager API (without SOLIDWORKS)
caption: Export Part File To Parasolid
description: Power Shell script to export part file to parasolid format (.xmp_bin) from command line via Document Manager API (without SOLIDWORKS)
image: export-parasolid.svg
labels: [export,parasolid]
group: Import/Export
---
此 PowerShell 脚本允许从命令行使用 SOLIDWORKS 文档管理器 API 将 SOLIDWORKS 零件文件导出为 Parasolid 格式（.xmp_bin）。

该文件可以在任何兼容的 CAD 应用程序中打开（如 SOLIDWORKS、Solid Edge 等）。

此脚本不需要安装 SOLIDWORKS，也不消耗 SOLIDWORKS 许可证。

## 配置和使用说明

* 创建两个文件，并从下面的代码片段中粘贴代码

### export-parasolid.ps1

{% code-snippet { file-name: export-parasolid.ps1 } %}

### export-parasolid.cmd

{% code-snippet { file-name: export-parasolid.cmd } %}

* 将 *SolidWorks.Interop.swdocumentmgr.dll* 复制到创建上述脚本的文件夹中。PowerShell 脚本基于 .NET Framework 2.0，因此 SOLIDWORKS 文档管理器互操作性必须针对此框架。该 dll 可在以下位置找到：**SOLIDWORKS 安装文件夹**\api\redist\CLR2\SolidWorks.Interop.swdocumentmgr.dll

或者，可以指定互操作性的完整路径，如下所示。在这种情况下，不需要将此 dll 复制到脚本文件夹中。

~~~ ps1
$Assem = ( 
   "SolidWorks.Interop.swdocumentmgr.dll 的完整路径"
    ) 
~~~

* 启动命令行并执行以下命令

~~~ bat
> [export-parasolid.cmd 的完整路径] [输入 SOLIDWORKS 文件的完整路径] [输出目录的完整路径]
~~~

结果是将文件的所有配置的所有实体导出到指定目录（如果目录不存在，则会自动创建）。输出文件的命名方式如下：*[原文件名]_[配置名称].xmp_bin*。进程日志直接显示在控制台中：

![Parasolid 导出控制台输出](export-parasolid-console-output.png)