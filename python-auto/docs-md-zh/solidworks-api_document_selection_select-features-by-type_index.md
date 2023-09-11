---
layout: sw-tool
title: 使用SOLIDWORKS API按类型选择SOLIDWORKS模型中的所有特征的宏
caption: 按类型选择特征
description: 使用VBA宏在活动的SOLIDWORKS模型（零件、装配或绘图）中选择所有特征，通过指定其类型
image: selected-3dsketches.png
labels: [选择,特征类型,多选,批量选择]
group: 模型
---
![在装配文档中选择的所有3D草图](selected-3dsketches.png){ width=250 }

这个VBA宏使用SOLIDWORKS API在活动模型（零件、装配或绘图）中选择所有特征。对于绘图和装配，还会选择子组件中的特征。

与[获取特征类型名称](/solidworks-api/document/features-manager/get-feature-type-name/)一起使用此宏，以获取用于过滤的所需特征类型名称。

## 配置

修改宏开头的常量

~~~ vb
Const APPEND_SELECTION As Boolean = False 'True表示追加选择，False表示清除现有选择
Const TYPE_NAME As String = "" '从特征中获取类型名称，请参考'获取特征类型名称'宏
~~~

此宏可与其他需要预先选择特征的宏一起使用。它还可以与SOLIDWORKS批量操作（如删除或抑制）一起使用。

{% code-snippet { file-name: Macro.vba } %}