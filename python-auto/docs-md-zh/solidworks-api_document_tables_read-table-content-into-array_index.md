---
title: 使用SOLIDWORKS API将表格内容读入数组
caption: 将表格内容读入数组
description: 本示例演示了如何使用SOLIDWORKS API将选定表格（物料清单、常规表格、切割清单表格等）的内容读入二维数组中。
labels: [数组, 物料清单, 读取, SOLIDWORKS API, 表格]
redirect-from:
  - /2018/03/solidworks-api-model-read-table-content-into-array.html
---
本示例演示了如何使用SOLIDWORKS API将选定表格（物料清单、常规表格、切割清单表格等）的内容读入二维数组中。

[SOLIDWORKS API接口ITableAnnotation](https://help.solidworks.com/2018/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.ITableAnnotation.html)提供了访问所有表格类型数据的功能。

{% code-snippet { file-name: Macro.vba } %}