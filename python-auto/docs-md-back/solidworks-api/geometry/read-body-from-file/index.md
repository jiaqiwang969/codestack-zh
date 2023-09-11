---
title: Read and display body from the file using SOLIDWORKS API
caption: Read Body From File
description: VBA example to deserialize body geometry from external binary file into temp body and display using SOLIDWORKS API
labels: [deserialize,com stream,temp body]
---
这个VBA示例演示了如何从外部二进制文件中读取实体几何数据。将这些数据加载到COM流中，并使用SOLIDWORKS API恢复到临时实体中。

实体将显示给用户，并停止宏执行。实体不会出现在特征管理器树中，只在图形区域中可见。

继续执行宏以销毁实体。

{% code-snippet { file-name: Macro.* } %}