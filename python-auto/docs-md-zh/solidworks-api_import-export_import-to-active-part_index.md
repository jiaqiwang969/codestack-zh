---
layout: article
caption: 导入到活动零件
title: 使用SOLIDWORKS API将外部文件导入活动零件的宏
description: 使用VBA宏将外部文件（parasolid、step、iges等）直接导入到活动零件文档中的SOLIDWORKS API
image: imported-file.png
---
![文件导入到活动零件文档](imported-file.png)

这个VBA宏演示了如何将带有实体的外部文件（例如parasolid、step、iges等）直接导入到活动零件文档中。

请在**INPUT_FILE**常量中更改导入文件的路径。

此宏仅支持将外部文件导入为零件文档。

{% code-snippet { file-name: Macro.vba } %}