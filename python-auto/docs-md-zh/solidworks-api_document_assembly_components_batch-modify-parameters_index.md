---
title: 使用SOLIDWORKS API修改组件的配置参数
caption: 修改多个组件的配置参数
description: 本示例演示了如何使用SOLIDWORKS API修改指定配置（例如抑制状态）中多个组件的参数。 
image: modify-configurations.png
labels: [参数，设计表，组件，配置]
---
![在配置中修改组件参数](modify-configurations.png){ width=350 }

本示例演示了如何使用参数（类似于设计表参数）来抑制除活动配置之外的所有配置中的所有组件，使用SOLIDWORKS API。不需要激活配置或选择任何组件来使用宏。

可以批量修改多个组件以提高性能。

{% code-snippet { file-name: Macro.vba } %}