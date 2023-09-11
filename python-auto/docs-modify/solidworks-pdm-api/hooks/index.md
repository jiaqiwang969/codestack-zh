---
title: Hooking the notifications in SOLIDWORKS PDM API
caption: Hooks
description: Articles and examples explaining how to use event hooks in SOLIDWORKS PDM add-in from API
labels: [hooks, add-in]
order: 6
---
SOLIDWORKS PDM在操作过程中会触发多个事件。这些事件包括但不限于：

* 检入和检出
* 工作流状态更改
* 数据卡值更改
* 文件操作：创建、添加、删除

SOLIDWORKS PDM API通过[IEdmAddIn5::OnCmd](https://help.solidworks.com/2018/english/api/epdmapi/epdm.interop.epdm~epdm.interop.epdm.iedmaddin5~oncmd.html)重载提供了对这些挂钩的访问。

本节将解释挂钩的使用，并提供使用SOLIDWORKS PDM API中挂钩的各种代码示例。