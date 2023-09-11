---
layout: sw-tool
title: Export SOLIDWORKS table to CSV using VBA macro
caption: Export Table To CSV
description: Macro exports selected table or specified tables (BOM, General Table, Revision etc.) into CSV format allowing to export with or without header preserving the special symbols like comma (,) and new line symbol using VBA macro
image: export-table-csv.svg
labels: [table,csv,export]
group: Model
---
该宏使用SOLIDWORKS API将选定的表格（或指定类型的表格）导出为CSV（逗号分隔值）文件。此功能类似于内置的“另存为”选项：

![表格的另存为选项](bom-save-as.png){ width=350 }

但是，该宏会保留逗号、引号或换行符等特殊符号，并根据CSV规范进行正确的转义：

![带有特殊符号（逗号和换行符）的BOM](bom-table.png){ width=350 }

因此，可以使用像MS Excel这样的CSV读取器正确读取该文件；

![导入Excel的CSV文件](bom-table-csv-excel.png){ width=350 }

对于上述示例的BOM表格，该宏将生成以下输出：

~~~ csv
项目编号,零件编号,描述,数量
1,B01-A57,刀轴,1
2,B01-A12,顶刀,1
3,B02,"底刀
固定",1
4,R1284,刀铆钉,4
5,E25-E16,"刀片延伸，塑料",1
~~~

## 配置

可以通过修改常量的值来配置宏

~~~ vb
Const OUT_FILE_PATH_TEMPLATE As String = "<_FileName_>-<_TableName_>.csv" '将空字符串保存在模型文件夹中
Const INCLUDE_HEADER As Boolean = True 'True包含表头，False仅包含数据
Const TABLE_TYPE As Integer = swTableAnnotationType_e.swTableAnnotation_BillOfMaterials  '-1使用选定的表格或在swTableAnnotationType_e中定义的表格类型（例如swTableAnnotationType_e.swTableAnnotation_BillOfMaterials导出所有BOM表格）
Const ALL_SHEETS As Boolean = False 'False仅从活动工作表导出

Const MERGE As Boolean = False 'True将所有表格合并到单个文件中
~~~

*OUT_FILE_PATH_TEMPLATE*可以是相对路径或绝对路径。如果指定了相对路径，文件将保存在与源文件相同的目录中

支持以下占位符：

* <\_FileName\_> - 源文件的名称
* <\_TableName\_> - 表格的名称
* <\_SheetName\_> - 表格所在的工作表的名称（仅适用于绘图）

如果使用**MERGE**选项，所有表格数据将输出到单个CSV文件中，每个表格之间用空行分隔。如果文件名模板使用了表格特定的占位符，则第一个表格将被用作模板。

## CAD+

该宏与[Toolbar+](https://cadplus.xarial.com/toolbar/)和[Batch+](https://cadplus.xarial.com/batch/)工具兼容，因此可以将按钮添加到工具栏并分配快捷键以便更方便地访问或批量运行。

要启用[宏参数](https://cadplus.xarial.com/toolbar/configuration/arguments/)，将**ARGS**常量设置为true

~~~ vb
#Const ARGS = True
~~~

在这种情况下，不需要复制宏来设置单独的[隐藏和显示选项](#configuration)。

而是使用**-bom**、**-general**、**-revision**、**-cutlist**作为第一个参数来指定要导出的表格类型，并将可选的输出文件模板作为第二个参数

例如，以下参数将将BOM表格导出为CSV格式，保存在D盘的**Tables**文件夹中，文件名为源表格的名称。

~~~
> -bom "D:\Tables\<_TableName_>.csv"
~~~

{% code-snippet { file-name: Macro.vba } %}
