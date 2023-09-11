---
layout: sw-tool
title: Macro to export SOLIDWORKS file to multiple formats
caption: Export To Multiple Formats
description: VBA macro to export file (or optionally all configuration or drawing sheets) to multiple formats
image: batch-export.svg
labels: [export]
group: Import/Export
---
![带有支持的格式列表的保存文件对话框](file-save-dialog.png){ width=500 }

此VBA宏允许将活动的SOLIDWORKS文档导出为SOLIDWORKS支持的多种格式。宏支持灵活的选项来指定文件路径，并允许同时导出多种格式。

如果目录不存在，宏将自动创建目录。

## 配置

可以通过修改**OUT_NAME_TEMPLATES**、**OUT_FOLDER**和**ALL_CONFIGS**常量来配置宏

### 输出名称模板

此常量允许指定导出文件的输出路径模板。它应包含定义导出格式的扩展名。

它可以是绝对路径，也可以是相对路径。如果是后者，则结果将保存在文件目录中，或者如果**OUT_FOLDER**常量不为空，则保存在指定的目录中。

> **OUT_FOLDER**可以作为[宏的参数](https://cadplus.xarial.com/macro-arguments/)传递

支持以下占位符

* <\_FileName\_> - 文档文件的名称（不包括扩展名）
* <\_ConfName\_> - 此文件的活动配置的名称。如果将**ALL_CONFIGS**选项设置为**True**，则会更改此名称
* <[PropertyName]> - 任何自定义属性的名称，用于读取值，例如\<PartNo\>将替换为自定义属性*PartNo*的值。属性将尝试从配置中读取，如果不可用，则使用通用属性。

占位符将在运行时解析。

通过在宏的开头使用**Array**函数填充常量来配置值。根据需要指定尽可能多的数组元素。

以下示例将活动文档导出为PDF、DXF和JPG，并将输出文件命名为**PartNo**自定义属性。文件将保存在与原始文件相同的文件夹中。

~~~ vb
Sub main()
        
    OUT_NAME_TEMPLATES = Array("<PartNo>.pdf", "<PartNo>.dxf", "<PartNo>.jpg")
~~~

以下示例将活动文件导出为parasolid格式，并保存到**D:\Exports**文件夹中。文件的名称与原始文件的名称相同。

~~~ vb
Sub main()
        
    OUT_NAME_TEMPLATES = Array("D:\Exports\<_FileName_>.x_t")
~~~

### 导出选项

可以通过更改**STEP_VERSION**常量的值来配置STEP格式的导出选项。将其设置为**214**以使用**AP214**格式，或将其设置为**203**以使用**AP203**格式。

~~~ vb
Const STEP_VERSION As Long = 214 '203 or 214
~~~

要导出3D PDF，请将**PDF_3D**常量设置为**True**

~~~ vb
Const PDF_3D As Boolean = True
~~~

### 将组件数量包含在文件名中

如果对装配体的所有组件运行此宏，则可能需要将BOM数量包含在文件名中。使用[SOLIDWORKS装配中的组件数量写入自定义属性](/solidworks-api/document/assembly/components/write-quantities/)宏。在导出之前，对装配体运行此宏，以创建具有数量值的自定义属性，然后使用**\<Qty\>**占位符将其包含在输出文件名中。

### 处理所有配置

如果将**ALL_CONFIGS**常量设置为**True**，宏将逐个激活所有配置（对于装配体和零件）或所有绘图页（对于绘图），然后运行导出命令。

## 故障排除

如果宏报告错误，在某些情况下，可能不会立即明确导致错误的原因，因为错误详细信息被异常处理程序“吞噬”了。为了禁用错误处理并显示导致错误的确切行，请在代码中的所有*On Error GoTo catch_*行之前放置撇号'符号，如下所示。

~~~ vb jagged
Sub main()
        
    Set swApp = Application.SldWorks
    
try_:
    'On Error GoTo catch_
~~~

请提交[错误报告](https://github.com/xarial/codestack/issues/new?labels=bug)，并附上此错误的快照和用于重现的模型（如果可能）

{% code-snippet { file-name: Macro.vba } %}