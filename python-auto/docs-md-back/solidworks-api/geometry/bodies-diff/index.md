---
title: SOLIDWORKS macro to find the geometrical difference between parts
caption: Part Geometry Diff
description: Diff tool to find the geometrical difference between multi-bodies parts using SOLIDWORKS API
image: part-bodies-diff.png
labels: [geometry, transform, diff, compare]
---
该宏允许通过其几何形状来比较两个零件。

使用[IBody2::GetCoincidenceTransform2](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.ibody2~getcoincidencetransform2.html) SOLIDWORKS API来比较体，并在相等时找到它们之间的变换。

### 注意事项

* 该宏支持多体零件
* 即使可比较的零件中的体位于不同的位置（即移动或旋转），该宏也会比较这些体。
* 可比较的零件可能具有不同数量的体
* 该宏将尝试找到两个零件之间最合适的变换

### 示例

要比较的原始零件：

![原始零件](original-part.png){ width=250 }

要比较的零件：

![要比较的零件](part-to-compare.png){ width=250 }

第二个零件具有修改后的几何形状，并在空间中重新定位。第二个零件中的一些体已被删除。

该宏计算出以下结果：

![结果差异文件](part-bodies-diff.png){ width=250 }

### 操作说明

* 打开原始零件文件
* 运行该宏。
* 指定要与之比较的零件文件的完整路径
* 结果将在原始零件中显示第二个零件
* 继续执行宏（F5）以清除预览

{% code-snippet { file-name: Macro.vba } %}