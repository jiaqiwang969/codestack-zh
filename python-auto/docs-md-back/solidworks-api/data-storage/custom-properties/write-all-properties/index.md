---
title: Write custom property to file, configuration and cut-list using SOLIDWORKS API
caption: Write All Properties
description: VBA macro example to write different types of properties (general, configuration specific and cut list) using SOLIDWORKS API
image: approved-date-custom-property.png
labels: [set property,add property,write property,date]
---
![日期自定义属性](approved-date-custom-property.png){ width=550 }

此VBA宏示例演示了如何使用SOLIDWORKS API将自定义属性（通用属性、配置特定属性和切割清单项（焊接或钣金）属性）添加（创建新的或更改现有的）到各种自定义属性源中。

宏添加了类型为“日期”的*ApprovedDate*自定义属性，并将值设置为当前日期。

> 由于某些原因，当分配给切割清单项时，自定义属性字段类型被忽略并默认为文本类型。

{% code-snippet { file-name: Macro.vba } %}