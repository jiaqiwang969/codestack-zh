---
标题：使用SOLIDWORKS API获取坐标系的转换矩阵
说明：VBA宏用于从选择的坐标系中提取4x4转换矩阵，并将结果输出到即时窗口中
图片：coordinate-system.png
标签：[转换，坐标系]
---
![特征管理器树中的坐标系](coordinate-system.png){ width=450 }

这个VBA宏从特征管理器树中选择的坐标系中提取4x4的[转换矩阵](/solidworks-api/geometry/transformation/)。

逗号分隔的结果将输出到VBA编辑器的即时窗口（Ctrl+G）中。

![矩阵输出到VBA编辑器的即时窗口](maxtrix-output-immediate.png){ width=350 }

{% code-snippet { file-name: Macro.vba } %}