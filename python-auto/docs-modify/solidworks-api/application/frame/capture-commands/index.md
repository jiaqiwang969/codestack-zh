---
layout: sw-tool
title: VBA macro to capture SOLIDWORKS commands via API event handlers
caption: Capture SOLIDWORKS Commands
description: Macro allows capturing SOLIDWORKS and user commands into the list box
image: capturing-hide-command-id.png
labels: [command, event]
group: Developers
---
该宏允许捕获SOLIDWORKS命令ID（例如工具栏、页面按钮或上下文菜单的点击）。命令在[swCommands_e](https://help.solidworks.com/2012/english/api/swcommands/solidworks.interop.swcommands~solidworks.interop.swcommands.swcommands_e.html)枚举中定义，并可以使用[SOLIDWORKS API](https://help.solidworks.com/2012/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isldworks~runcommand.html)中的[ISldWorks::RunCommand](https://help.solidworks.com/2012/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isldworks~runcommand.html)方法调用。

当SDK中某些SOLIDWORKS API不可用时，这可能特别有用。

所有命令都有用户友好的名称，但它们不一定与用户界面中的名称匹配。这一事实可能会使查找正确的命令变得困难（因为当前有超过3000个可用命令）。例如，用户界面中的隐藏草图命令对应于*swCommands_Blank_Refgeom*命令ID。

## 捕获标准命令

该宏可以通过单击所需命令直接从SOLIDWORKS中捕获命令ID。

* 运行宏。显示带有列表的窗体。
* 执行所需操作（例如单击按钮或菜单项）。
* 命令ID将被记录并显示在列表中。

![捕获隐藏草图命令ID](capturing-hide-command-id.png){ width=350 }

可以在[命令列表](https://help.solidworks.com/2012/english/api/swcommands/solidworks.interop.swcommands~solidworks.interop.swcommands.swcommands_e.html)中查找命令ID。

![swCommands_e枚举中的隐藏草图命令ID](sw-commands-id.png){ width=350 }

> 不需要显式使用[swCommands_e](https://help.solidworks.com/2012/english/api/swcommands/solidworks.interop.swcommands~solidworks.interop.swcommands.swcommands_e.html)枚举，因为它在另一个互操作性（*solidworks.interop.swcommands.dll*）中定义。相反，命令ID可以定义为整数或自定义枚举。

## 从自定义加载项中捕获命令

对于标准SOLIDWORKS命令，用户命令参数将等于0。但是，无法为任何自定义加载项或[宏按钮](/solidworks-api/getting-started/macros/macro-buttons/)定义命令。

如果单击此命令，命令ID将等于以下之一：

![用户特定命令ID](user-commands.png){ width=450 }

命令将指示按钮的类型（最小化工具栏、菜单、宏按钮等），而用户命令ID将等于自定义按钮的用户ID。这是可以通过在SOLIDWORKS加载项中创建自定义命令管理器时通过[ICommandGroup::CommandId](https://help.solidworks.com/2012/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.ICommandGroup~CommandID.html)属性检索的命令用户ID。

![从自定义加载项中捕获命令](capturing-user-command-id.png){ width=250 }

## 创建宏

* 将用户窗体模块添加到宏中，并将其命名为*CommandsMonitorForm*

![VBA项目结构](vba-macro-project.png){ width=450 }

* 将列表框控件拖放到窗体上，并将其命名为*lstLog*

![将列表框控件添加到窗体](add-list-box-control.png){ width=450 }

* 将代码添加到相应的模块中

**宏**

{% code-snippet { file-name: Macro.vba } %}

**CommandsMonitorForm**

{% code-snippet { file-name: CommandsMonitorForm.vba } %}