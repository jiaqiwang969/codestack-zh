---
title: 使用SOLIDWORKS API获取图纸体几何类型
caption: 获取图纸体几何类型
description: 该示例用于识别所选图纸体的类型（开放壳体、内部壳体、外部壳体）
image: face-shell-types.png
labels: [示例, 面, 几何, 开放几何, 壳体, solidworks api, 拓扑]
redirect-from:
  - /2018/03/solidworks-api-geometry-get-body-geometry-type.html
---
在SOLIDWORKS体中有3种类型的面：

* **开放壳体**。与相连面一起，不形成封闭几何体的图纸体面（例如平面面，而壳体立方体或球体的面不会被视为开放）
* **内部壳体**。属于实体体中的空腔的面。
* **外部壳体**。不属于前两组的其他面。

![面的壳体类型](face-shell-types.png){ width=400 height=243 }

下面的示例使用SOLIDWORKS API来识别所选图纸体的类型。如果图纸体是开放几何（包含开放壳体面）或封闭几何（没有开放壳体面），则可以将封闭几何图纸体转换为实体体。

{% code-snippet { file-name: SolidWorksMacro.cs } %}