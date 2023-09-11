---
title: 使用SOLIDWORKS API读取和显示文件中的实体
caption: 从文件中读取实体
description: VBA示例，使用SOLIDWORKS API将外部二进制文件中的实体几何数据反序列化为临时实体并显示出来
labels: [反序列化, COM流, 临时实体]
---
这个VBA示例演示了如何从外部二进制文件中读取实体几何数据。将这些数据加载到COM流中，并使用SOLIDWORKS API恢复到临时实体中。

实体将显示给用户，并停止宏执行。实体不会出现在特征管理器树中，只在图形区域中可见。

继续执行宏以销毁实体。

{% code-snippet { file-name: Macro.* } %}