---
layout: sw-tool
title: 从SOLIDWORKS零件或装配组件导出展开图案
caption: 从零件或装配组件导出展开图案
description: VBA宏，用于从活动装配或活动零件的所有组件中导出展开图案
image: assembly-flat-pattern.svg
labels: [使用位置,父级,组件]
group: 导入/导出
redirect-from:
    - /solidworks-api/document/sheet-metal/export-assembly-components/
---
此VBA宏允许从活动SOLIDWORKS装配或活动零件文档中的所有钣金组件导出所有展开图案到DXF/DWG。

宏允许灵活指定输出文件的名称，可以使用占位符（原始文件名、特征名、自定义属性、切割列表自定义属性等）与自由文本结合，并支持指定子文件夹。

导出完成后，将显示以下消息框。

![导出完成时显示的消息框](operation-completed.png)

{%youtube id: FtXkdSlekG8 %}

## 配置

可以通过修改**OUT_NAME_TEMPLATE**和**FLAT_PATTERN_OPTIONS**常量来配置宏

### 输出名称模板

此常量允许指定展开图案的输出路径模板。

这可以是绝对路径或相对路径。如果是后者，则结果将相对于装配目录保存。

扩展名（.dxf或.dwg）必须作为命名模板的一部分指定

支持以下占位符

* <\_FileName\_> - 展开图案所在的零件文件的名称（不包括扩展名）
* <\_FeatureName\_> - 展开图案特征的名称
* <\_ConfName\_> - 此展开图案的配置名称（即组件的引用配置）
* <\_AssmFileName\_> - 主装配的名称
* <$CLPRP:[属性名]> - 任何切割列表属性的名称，用于读取值，例如\<Thickness\>将替换为切割列表自定义属性*Thickness*的值
* <$PRP:[属性名]> - 任何钣金零件的自定义属性的名称，用于读取值，例如\<PartNo\>将替换为切割列表自定义属性*PartNo*的值
* <$ASSMPRP:[属性名]> - 主装配的任何自定义属性的名称，用于读取值，例如\<ProductId\>将替换为切割列表自定义属性*ProductId*的值

占位符将在运行时为每个展开图案解析。

例如，以下值将使用零件文档的名称将展开图案保存在与主装配相同文件夹中的*DXFs*子文件夹中

~~~ vb
Const OUT_NAME_TEMPLATE As String = "DXFs\<_FileName_>.dxf"
~~~

而以下名称将将所有展开图案保存为DWG文件到*D*驱动器中的*Output*文件夹中，其中文件名将从每个相应展开图案的*PartNo*属性中提取。

~~~ vb
Const OUT_NAME_TEMPLATE As String = "D:\Output\<$CLPRP:PartNo>.dwg"
~~~

以下设置将创建与切割列表中的**Thickness**自定义属性值相对应的子文件夹，并使用从主装配中提取的**ProductName**自定义属性值，后跟下划线符号和来自钣金零件文档的**PartNo**属性值的文件名。

~~~ vb
Const OUT_NAME_TEMPLATE As String = "D:\Output\<$CLPRP:Thickness>\<$ASSMPRP:ProductName>_<$PRP:PartNo>.dwg"
~~~

### 在文件名中包含数量

此宏没有明确的变量来将展开图案的数量包含在文件名中。但是，可以通过包含自动**QUANTITY**自定义属性的值与**<$CLPRP:QUANTITY>**占位符来提取多体钣金零件的数量值。

为了在装配中包含组件数量，请使用[将SOLIDWORKS装配中的组件数量写入自定义属性](/solidworks-api/document/assembly/components/write-quantities/)宏。在导出之前运行此宏以创建具有数量值的自定义属性，然后使用**<$CLPRP:Qty>**占位符将其包含到输出文件名中。

> 注意，此宏不会将多体钣金零件的数量与组件数量相乘

### 展开图案选项

可以通过指定**FLAT_PATTERN_OPTIONS**的值来配置选项。使用**+**来组合选项

![展开图案导出选项](flat-pattern-export-options.png)

例如，要导出隐藏边、库特征和成型工具，请使用以下设置。

~~~ vb
Const FLAT_PATTERN_OPTIONS As Integer = SheetMetalOptions_e.IncludeHiddenEdges + SheetMetalOptions_e.ExportLibraryFeatures + SheetMetalOptions_e.ExportFormingTools
~~~

> 注意，必须始终指定几何选项，因为它是展开图案导出所必需的

## 跳过已创建的文件

**SKIP_EXISTING_FILES**选项允许指定如果输出文件已经存在，宏是否应重新生成输出文件。

将此选项设置为true以跳过导出文件（.dxf或.dwg），如果目标位置上已存在输出文件。

~~~ vb
Const SKIP_EXISTING_FILES As Boolean = True
~~~

当处理大型装配时，此选项可能很有用，并且需要在SOLIDWORKS重新启动后继续执行。导出展开图案是一项性能消耗很大的操作，因此在处理大型作业时，SOLIDWORKS可能会崩溃或挂起。此选项可以帮助在重新启动后继续导出。

## 故障排除

如果宏报告错误，在某些情况下，可能不会立即明确导致错误的原因，因为错误详细信息被异常处理程序“吞噬”了。为了禁用错误处理并显示导致错误的确切行，请在代码中的所有*On Error GoTo catch_*行之前放置撇号'符号，如下所示。

~~~ vb jagged
Sub main()
        
    Set swApp = Application.SldWorks
    
try_:
    'On Error GoTo catch_
~~~

~~~ vb jagged
Sub ExportFlatPattern(part As SldWorks.PartDoc, flatPattern As SldWorks.Feature, outFilePath As String, opts As SheetMetalOptions_e, conf As String)
    
    Dim swModel As SldWorks.ModelDoc2
    Set swModel = part
    
    Dim error As ErrObject
    Dim hide As Boolean

try_:
    
    'On Error GoTo catch_
~~~

请提交[错误报告](https://github.com/xarial/codestack/issues/new?labels=bug)，并附上此错误的快照和用于重现的模型（如果可能）

## 注意事项

* 如果有轻量级组件，宏将要求解析它们。如果未解析组件，则宏可能会生成错误
* 将导出每个多体钣金零件的每个展开图案。确保使用<\_FeatureName\_>或<$CLPRP:[属性名]>来区分结果文件
* $PRP和$ASSMPRP值将首先从配置特定属性中提取，如果为空，则从一般文件属性中提取
* 如果指定的属性不存在（对于$CLPRP、$PRP和$ASSMPRP），则使用空字符串作为占位符值
* 宏将处理所有不同的组件（文件路径+配置）
* 宏将自动创建所需的文件夹
* 宏将使用\_替换所有路径无效的符号
* 宏将仅导出分组在切割列表下的唯一实体，并跳过属于已导出切割列表的展开图案

{% code-snippet { file-name: Macro.vba } %}
