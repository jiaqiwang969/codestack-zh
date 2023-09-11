---
title: Defining commands buttons in SOLIDWORKS toolbar using SwEx.AddIn framework
caption: Defining Commands
description: Explanations on the ways of defining the commands in groups using SwEx framework for SOLIDWORKS add-ins in C# and VB.NET
toc-group-name: labs-solidworks-swex
order: 1
---
## 定义命令

SwEx框架允许在枚举(enum)中定义命令。在这种情况下，枚举值将成为相应命令的ID。

{% code-snippet { file-name: CommandsManager.DefiningCommands.* } %}

## 命令装饰

可以使用附加属性来装饰命令，以定义命令的外观和感觉。

### 标题
可以使用[TitleAttribute](https://docs.codestack.net/swex/common/html/T_CodeStack_SwEx_Common_Attributes_TitleAttribute.htm)来定义用户友好的标题。或者，任何继承[DisplayNameAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.displaynameattribute?view=netframework-4.0)的属性类都可以作为标题。

### 描述
描述是当用户将鼠标悬停在命令上时在SOLIDWORKS命令栏中显示的文本。可以使用[DescriptionAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.descriptionattribute?view=netframework-4.0)来定义描述。

### 图标
可以使用[CommandIconAttribute](https://docs.codestack.net/swex/add-in/html/T_CodeStack_SwEx_AddIn_Attributes_CommandIconAttribute.htm)来设置图标。该属性有多个重载。用户可以提供：

* 单个主图标
* 2个图标（小图标和大图标）
* 6个高分辨率图标（从SOLIDWORKS 2016开始支持）

也可以使用通用的[IconAttribute](https://docs.codestack.net/swex/common/html/T_CodeStack_SwEx_Common_Attributes_IconAttribute.htm)来指定图标。

无论选择了上述哪个选项，SwEx框架都会根据SOLIDWORKS的版本适当地缩放图标。例如，如果为SOLIDWORKS 2016及更高版本指定了单个主图标，则会创建6个图标以支持高分辨率，对于旧版本的SOLIDWORKS，将创建2个图标（大图标和小图标）。如果用户指定了6个图标-所有这些图标都将在SOLIDWORKS 2016或更新版本中按原样使用，但在旧版本中它们将被转换为2个（小图标和大图标），因为SOLIDWORKS不支持高分辨率图标。

支持透明度。SwEx框架将自动为与SOLIDWORKS兼容性所需的透明度键分配透明度。

图标可以从任何静态类引用。通常应该是一个资源类。需要将资源类的类型指定为第一个参数，并将资源名称指定为附加参数。使用*nameof*关键字加载资源名称，以避免使用'魔术'字符串。

{% code-snippet { file-name: CommandsManager.CommandsAttribution.* } %}

## 命令范围

每个命令可以分配操作范围（即可以执行该命令的环境，例如零件、装配等）。可以使用[CommandItemInfoAttribute](https://docs.codestack.net/swex/add-in/html/T_CodeStack_SwEx_AddIn_Attributes_CommandItemInfoAttribute.htm)属性来分配范围，通过在属性的构造函数的*suppWorkspaces*参数中指定值。[swWorkspaceTypes_e](https://docs.codestack.net/swex/add-in/html/T_CodeStack_SwEx_AddIn_Enums_swWorkspaceTypes_e.htm)是一个标志枚举，因此可以组合工作区。

框架将根据指定的范围自动禁用/启用命令，根据活动环境进行适配。有关分配状态的其他逻辑，请参阅[自定义启用命令状态](/labs/solidworks/swex/add-in/commands-manager/command-states/)文章。

{% code-snippet { file-name: CommandsManager.CommandsScope.* } %}

## 用户分配的命令组ID

[CommandGroupInfoAttribute](https://docs.codestack.net/swex/add-in/html/T_CodeStack_SwEx_AddIn_Attributes_CommandGroupInfoAttribute.htm)允许将静态命令ID分配给组。这应该应用于枚举器定义。如果不使用此属性，SwEx框架将自动分配ID。

{% code-snippet { file-name: CommandsManager.CommandGroupId.* } %}