---
layout: sw-tool
title: Macro for components configurations permutation using SOLIDWORKS API
caption: Components Configurations Permutation
description: Macro performs a permutation for each components in the root level of the assembly using SOLIDWORKS API and saves the results as individual files
image: component-configurations.png
labels: [permutation,component,generation,configuration]
group: Assembly
---
该宏使用SOLIDWORKS API对每个顶层组件配置的组合（排列）生成装配体。

![组件配置](component-configurations.png){ width=450 }

生成的组合将保存为外部装配体（每个组合一个文件）。

![为每个组件配置的组合生成的装配体](generated-permutation-assemblies.png){ width=350 }

## 选项
* *OUT_FOLDER* - 输出文件夹的完整路径，结果文件将保存在此处

~~~ vb
Const OUT_FOLDER As String = "输出文件夹路径"
~~~

* *PERMUTE_ASSEMBLY_CONF* 选项允许指定是否在排列中使用装配体的配置，还是仅使用组件的配置

~~~ vb
Const PERMUTE_ASSEMBLY_CONF As Boolean = True 'True表示包括装配体配置，false表示仅包括组件配置
~~~

## 注意事项

* 运行该宏后，组件的原始状态将不会恢复。建议以只读方式打开装配体。
* 文件总数等于{组件1的配置数}x{组件2的配置数}x...x{组件n的配置数}

{% code-snippet { file-name: Macro.vba } %}