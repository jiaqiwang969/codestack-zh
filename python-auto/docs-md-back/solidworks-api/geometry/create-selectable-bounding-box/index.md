---
layout: sw-tool
title: Create selectable 3D bounding box sketch using SOLIDWORKS API
caption: Create Selectable Bounding Box
description: VBA macro which creates 3D bounding box sketch based on the SOLIDWORKS bounding box with an ability to select sketch segments
image: bounding-box.svg
labels: [bounding box]
group: Geometry
---
![边界框草图](bounding-box-sketch.png){ width=450 }

SOLIDWORKS可以在零件文档中插入3D边界框。然而，这个边界框的边缘（线段）不能被选择和用于建模目的。

这个VBA宏基于SOLIDWORKS 3D边界框创建一个边界框草图。草图中的所有线段都可以被选择和用于参考或几何创建。

## 注意事项

* 宏将使用现有的3D边界框，如果不存在则创建新的边界框
* 生成的边界框在原始边界框更改后（重建后）会自动更新
    * 原始边界框必须可见以更新派生边界框

{% code-snippet { file-name: Macro.vba } %}