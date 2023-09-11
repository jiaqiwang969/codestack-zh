---
layout: sw-tool
title: 从SOLIDWORKS文档中删除所有颜色的宏
caption: 从零件中删除所有颜色
description: 该宏演示了如何使用SOLIDWORKS API从零件或装配文档的所有层级（面、特征、实体、模型）中删除所有颜色
image: remove-colors.svg
labels: [删除颜色, 外观, 材料属性]
group: 零件
---
![零件文档中的外观层级](material-properties-levels.png){ width=250 }

该宏使用SOLIDWORKS API从所有层级（面、特征、实体、模型）中删除零件文档中的所有颜色。

该宏可以配置为从所有配置或仅活动配置中删除颜色。可以通过更改宏开头的以下常量的值来设置此选项：

~~~ vb
Const REMOVE_FROM_ALL_CONFIGS As Boolean = True 'True表示从所有配置中删除，False表示仅从活动配置中删除
~~~

{% code-snippet { file-name: Macro.vba } %}