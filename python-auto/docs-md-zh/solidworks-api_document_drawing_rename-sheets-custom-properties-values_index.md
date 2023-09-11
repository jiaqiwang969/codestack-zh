---
layout: sw-tool
title: 使用自定义属性值重命名SOLIDWORKS图纸工作表
caption: 使用自定义属性值重命名图纸工作表
description: 该宏将使用SOLIDWORKS API根据指定的自定义属性值重命名所有图纸工作表
image: drw-sheets.png
labels: [自定义属性, 图纸, 示例, 宏, 属性, 重命名, 工作表, solidworks api, vba]
group: 图纸
redirect-from:
  - /2018/03/document_8.html
---
该宏将使用SOLIDWORKS API根据指定的自定义属性值重命名所有图纸工作表。

![图纸中的工作表列表](drw-sheets.png){ width=320 }

* 打开图纸并运行宏
* 指定要读取值的属性

![输入属性名称的弹出窗口](get-prp-name.png){ width=320 }

* 所有工作表将根据此属性的值进行重命名。宏将从工作表属性中指定的模型视图中获取该值。
不支持“与文档属性中指定的工作表相同”的选项。
如果选择了此选项，则将使用第一个视图的属性。
宏将尝试读取配置特定的属性，如果未指定属性，则读取模型级属性。

![在工作表属性中使用模型的自定义属性值选项](use-custom-prps-from-view-sheet-property.png){ width=400 }

{% code-snippet { file-name: Macro.vba } %}