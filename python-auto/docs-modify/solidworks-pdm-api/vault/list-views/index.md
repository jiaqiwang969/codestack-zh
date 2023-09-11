---
title: List all vault views using SOLIDWORKS PDM API
caption: List All Views
description: Example demonstrates how to list all available vault views and their paths using SOLIDWORKS PDM API
image: pdm-vaults-list.png
labels: [vault, view]
---
![将保险库视图信息打印到控制台窗口](pdm-vaults-list.png){ width=250 }

本示例演示了如何列出所有可用的保险库视图及其路径，并将信息打印到控制台窗口。

使用[IEdmVault8::GetVaultViews](https://help.solidworks.com/2018/english/api/epdmapi/epdm.interop.epdm~epdm.interop.epdm.iedmvault8~getvaultviews.html) SOLIDWORKS PDM API来列出所有可用的PDM保险库的信息。此外，也可以从注册表中获取这些信息。

{% code-snippet { file-name: Console.cs } %}