---
caption: Batch Export Models
title: Batch export SOLIDWORKS models via vbScript
description: Example of batch exporting SOLIDWORKS documents from the vbScript
---
这个示例演示了如何使用 vbScript 批量导出 SOLIDWORKS 文档

## 参数

1. SOLIDWORKS 模型所在文件夹的路径
1. 输入文件扩展名的过滤器
1. 输出文件夹的路径
1. 输出格式的扩展名

~~~
> "export-sw-models.vbs" "C:\Models" sldprt "C:\Output" step
~~~

{% code-snippet { file-name: export-sw-models.vbs } %}