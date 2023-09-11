---
title: SOLIDWORKS PDM API example for handling the data card button click
caption: DataCard Button Click
description: Collection of examples and articles explaining how to handle the button click on data card using SOLIDWORKS PDM Professional API
labels: [hooks, button click, datacard]
---
通过在按钮点击处理程序中提供自定义逻辑，可以使用SOLIDWORKS PDM API扩展数据卡的功能。与其他事件类似，按钮点击可以在[IEdmAddIn5::OnCmd](https://help.solidworks.com/2018/english/api/epdmapi/epdm.interop.epdm~epdm.interop.epdm.iedmaddin5~oncmd.html)重载中处理。

在设置数据卡时，用户需要在选项中分配特殊标签，然后可以作为注释从插件中读取，以便识别特定的按钮。

本节包含使用SOLIDWORKS PDM API和实现数据卡按钮点击事件的自定义行为的代码示例。