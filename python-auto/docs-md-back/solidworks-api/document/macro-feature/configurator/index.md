---
layout: sw-tool
title: Macro feature to configure model dimensions
caption: Model Configurator
description: VBA macro feature which allows to configure the dimensions of the model via custom user Form
image: part-configurator.svg
labels: [configure, macro feature, dimensions]
group: Model
---
这个VBA宏利用宏特性的功能，为指定的尺寸创建自定义模型配置器。

{% youtube id: JbcYEL9GY_c %}

宏将为指定的尺寸构建动态用户界面，并直接将**配置器**特性插入到特征管理器树中。

![配置模型尺寸](configuring-model.png)

可以随时通过点击**编辑特征**命令来修改设计。

![通过配置器表单编辑模型尺寸](edit-feature.png)

特征也可以在装配上下文中进行编辑。

![在装配上下文中编辑配置](in-context-editing.png)

要插入该特征，预先选择要配置的尺寸并运行宏。

对于每个选择的尺寸，指定用户友好的标题（将显示在表单上）：

![为尺寸指定标题](specify-dimension-title.png)

插入后，编辑特征的定义以更新模型。

配置器特性可以插入到零件或装配体中（包括插入到在装配上下文中编辑的组件中）。

尺寸将在活动配置或组件的引用配置中进行修改（如果在上下文中进行编辑）。

将配置器特性添加到装配体时，可以修改任何子组件的尺寸。

## 配置

用户可以修改下面的常量来更改一些参数。

* **BASE_NAME**常量定义了配置器特性的默认名称
* **EMBED_MACRO_FEATURE**允许将代码直接嵌入到模型中，这样它就不再与原始宏关联。可以与任何人共享并在不提供原始宏的情况下进行编辑

~~~ vb
Public Const BASE_NAME As String = "MyConfigurator" '配置器特性的默认名称

Const EMBED_MACRO_FEATURE As Boolean = True' 将宏特性嵌入到模型中
~~~

## 优势对比

下表演示了与其他流行的设计自动化方法和工具相比，这种方法的优势。

> 注意，下表仅显示了此宏与其他方法相比的优势。其他方法具有更多的优势和功能，而这些未包含在下表中。

| 特性  | 该宏 | 方程式  | 设计表  | DriveWorks |
|---|---|---|---|---|
| 安装简单  | &check;  | &check;  | &check;  | &cross;  |
| 输入方法简单  | &check;  | &cross;  | &cross;  | &check;  |
| 性能  | &check;  | &check;  | &cross;  | &cross;  |
| 需求编辑  | &check;  | &check;  | &check;  | &cross;  |
| 支持子组件  | &check;  | &cross;  | &cross;  | &check;  |
| 上下文编辑  | &check;  | &cross;  | &cross;  | N/A  |
| 可扩展性  | &check;  | &cross;  | &cross;  | &check;  |

### 安装简单

该标准定义了配置器的创建速度。DriveWorks需要特定的技能和规则引擎来创建配置器，而这个宏只需要预先选择尺寸。

### 输入方法简单

该标准定义了根据配置器输入参数应用和更改尺寸的简易程度。这个宏和DriveWorks都将使用自定义表单来简化输入，而方程式和设计表没有特定的输入表单，需要在其他方程式和定义的列表中搜索特定的输入。

### 性能

该标准定义了执行性能（应用参数之前需要多长时间）。这个宏直接将参数应用到尺寸上，立即生效。设计表需要加载Excel实例并打开文件以重新计算和应用值。DriveWorks将根据规格输入始终生成新模型。

### 需求编辑

该标准定义了是否可以更改现有设计的参数。DriveWorks会生成新模型，不会修改现有模型。

### 支持子组件

该标准定义了是否可以修改子组件的参数。虽然方程式可以为组件定义，但这些方程式不是配置特定的，即不可能有两个具有不同配置和不同方程式值的组件实例。

### 上下文编辑

该标准定义了是否可以使用上下文编辑从顶层装配中更改组件的配置。除了这个宏之外的所有方法都需要将目标组件在自己的窗口中打开才能进行编辑，而这个宏允许上下文编辑。

### 可扩展性

该标准定义了超出开箱即用功能的扩展性。方程式和设计表是内置功能。DriveWorks提供API并可扩展。这个宏是开源的，可以使用SOLIDWORKS API进行扩展。

## 宏设置

* 创建新的宏并复制下面的代码：

{% code-snippet { file-name: Macro.vba } %}

添加新的[用户表单](/visual-basic/user-forms/)并将下面的代码放入表单的代码后面

{% code-snippet { file-name: ConfiguratorForm.vba } %}

将表单的名称指定为**ConfiguratorForm**。结果，VBA中的解决方案树如下所示：

![VBA宏文件树](vba-solution-tree.png)