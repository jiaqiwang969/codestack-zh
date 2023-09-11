---
title: Modify configuration parameters for components using SOLIDWORKS API
caption: Modify Configuration Parameters For Multiple Components
description: Example demonstrates how to modify parameters of multiple components in the specified configurations (e.g. suppression state) using SOLIDWORKS API
image: modify-configurations.png
labels: [parameters, design table, components, configuration]
---
![在配置中修改组件参数](modify-configurations.png){ width=350 }

本示例演示了如何使用参数（类似于设计表参数）来抑制除活动配置之外的所有配置中的所有组件，使用SOLIDWORKS API。不需要激活配置或选择任何组件来使用宏。

可以批量修改多个组件以提高性能。

{% code-snippet { file-name: Macro.vba } %}