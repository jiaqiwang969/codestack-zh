---
layout: sw-tool
title: SOLIDWORKS宏将数据从Excel表复制到常规表格中
caption: 将数据从Excel表写入常规表格
description: 该宏将使用SOLIDWORKS API从指定的Excel电子表格中读取所有数据，并将其导入到活动文档的新常规表格中，或者更新现有表格
image: excel-to-table.svg
labels: [表格注释, Excel, 常规表格, 二维数组]
group: 模型
---
该宏将使用SOLIDWORKS API从指定的Excel电子表格中读取数据，并将其写入活动文档中新创建的常规表格中。

在宏的头部定义的常量中指定Excel文件的完整路径和电子表格的名称。

如果要更新现有的常规表格而不是创建新的表格，请在图形视图或特征管理器树中选择常规表格，然后运行该宏。

该宏可以嵌入到[宏特征](/solidworks-api/document/macro-feature)中，从而实现表格的自动更新。有关此选项的更多信息，请参阅[将常规表格链接到Excel并自动更新](/solidworks-api/document/macro-feature/general-table-link-excel/)。

![将采购订单数据导入到SOLIDWORKS常规表格的Excel表格](excel-table-to-sw-general-table.png){ width=500 }

{% code-snippet { file-name: Macro.vba } %}