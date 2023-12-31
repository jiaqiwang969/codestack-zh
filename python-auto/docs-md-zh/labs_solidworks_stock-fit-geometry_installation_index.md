---
title: Installation Guide for Stock Master add-ins for SOLIDWORKS
caption: Installation Guide
description: Instructions of installing of Stock Master add-in for SOLIDWORKS which provides additional features for packaging and stocking
toc-group-name: labs-solidworks-stock-master
order: 2
---
要安装插件，请在[此链接v. 0.5.0 (beta 1)](https://github.com/codestackdev/stock-fit-geometry/releases/tag/beta1)下载最新的msi安装程序（*StockMaster.msi*）。

## 注意
如果已安装旧版本的插件（v. 0.0.3或更早版本），需要按照以下步骤手动卸载先前的版本：

* 导航到先前版本的安装文件夹（路径可以通过在SOLIDWORKS的“工具->加载项...”菜单中将鼠标悬停在*Stock Fit Geometry*插件上找到）
* 从命令行运行以下命令（可能需要以管理员身份运行命令行）。将*FULL PATH TO CodeStack.StockFit.Sw.dll*替换为相应的dll的完整路径。

~~~ bat
"%Windir%\Microsoft.NET\Framework64\v4.0.30319\regasm" /codebase /u "FULL PATH TO CodeStack.StockFit.Sw.dll"
~~~
* 删除该文件夹

对于以后的任何版本，不需要执行此过程。