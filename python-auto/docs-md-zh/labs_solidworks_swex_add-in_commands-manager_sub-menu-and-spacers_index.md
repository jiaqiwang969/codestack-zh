---
title: 使用SwEx.AddIn在SOLIDWORKS命令管理器中添加子菜单和间隔符
caption: 子菜单和间隔符
description: 使用SwEx.AddIn框架在SOLIDWORKS命令管理器中添加子菜单和间隔符或命令选项卡框
image: sub-menu-and-spacer.png
toc-group-name: labs-solidworks-swex
order: 3
---
## 添加间隔符

可以通过使用[CommandSpacerAttribute](https://docs.codestack.net/swex/add-in/html/T_CodeStack_SwEx_AddIn_Attributes_CommandSpacerAttribute.htm)来装饰命令，从而在命令之间添加间隔符。间隔符将添加在此命令之前。

{% code-snippet { file-name: CommandsManager.Spacer.* } %}

如果为此命令组创建了命令选项卡框（即在[CommandItemInfoAttribute](https://docs.codestack.net/swex/add-in/html/M_CodeStack_SwEx_AddIn_Attributes_CommandItemInfoAttribute__ctor_2.htm)中将*showInCmdTabBox*参数设置为*true*），则间隔符不会反映在相应的命令选项卡框中。

## 添加子菜单

可以通过调用[CommandGroupInfoAttribute](https://docs.codestack.net/swex/add-in/html/M_CodeStack_SwEx_AddIn_Attributes_CommandGroupInfoAttribute__ctor_2.htm)属性的相应重载，并指定父菜单组的类型来定义命令组的子菜单。

{% code-snippet { file-name: CommandsManager.SubMenu.* } %}

子菜单在命令选项卡中以单独的选项卡框呈现。

## 示例

{% code-snippet { file-name: CommandsManager.SpacerAndSubMenu.* } %}

上述命令配置将创建以下菜单和命令选项卡框：

![子菜单和间隔符](sub-menu-and-spacer.png)

* Command1和Command2是在Commands_e枚举中定义的顶级菜单的命令
* 在Command1和Command2之间添加了间隔符
* SubCommand1和SubCommand2是在SubCommands_e枚举中定义的Commands_e枚举的子菜单的命令

![命令选项卡框](command-tab.png)

* 所有命令（包括子菜单命令）都添加在同一个命令选项卡中
* Command1和Command2分别放置在SubCommand1和SubCommand2的单独命令选项卡框中
* Command1和Command2之间的间隔符在命令选项卡中被忽略