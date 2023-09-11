---
layout: article
caption: Import To Active Part
title: Macro to import foreign file into active part using SOLIDWORKS API
description: VBA macro to import foreign file (parasolid, step, iges, etc.) directly into the active part document using SOLIDWORKS API
image: imported-file.png
---
![文件导入到活动零件文档](imported-file.png)

这个VBA宏演示了如何将带有实体的外部文件（例如parasolid、step、iges等）直接导入到活动零件文档中。

请在**INPUT_FILE**常量中更改导入文件的路径。

此宏仅支持将外部文件导入为零件文档。

{% code-snippet { file-name: Macro.vba } %}