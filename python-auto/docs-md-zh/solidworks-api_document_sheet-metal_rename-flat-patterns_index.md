---
layout: sw-tool
title: 在切割清单特征之后重命名钣金平板图案特征
caption: 在切割清单之后重命名平板图案
description: VBA宏，将钣金平板图案特征重命名为相应的切割清单特征名称
image: flat-pattern.svg
labels: [切割清单,钣金,平板图案,重命名]
group: 零件
---
![切割清单和钣金平板图案](renamed-flat-patterns.png){ width=250 }

这个VBA宏将所有的钣金平板图案特征重命名为相应的切割清单项目的名称。

此宏可以与[重命名切割清单特征](/solidworks-api/document/cut-lists/rename-cut-list-items/)宏一起使用。

为了避免名称冲突，平板图案特征会添加后缀，如下所示。

~~~ vb jagged-bottom
Const SUFFIX As String = "_FP"
~~~

当有多个平板图案共享同一个切割清单时，宏会自动为平板图案名称添加索引。

观看[视频演示](https://youtu.be/jsjN8zNRTuc?t=276)

{% code-snippet { file-name: Macro.vba } %}