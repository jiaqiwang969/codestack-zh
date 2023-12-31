---
layout: sw-tool
title: Macro to scale drawing views based on the geometry size using SOLIDWORKS API
caption: Scale Views Based On Geometry Size
description: VBA macro to scale drawing views in the current sheet based on the geometry size and specified map
image: scale-view.svg
labels: [scale,size,bounding box]
group: Drawing
---
![绘图视图缩放选项](drawing-view-scale.png){ width=250 }

这个VBA宏会根据几何尺寸和指定的匹配映射自动缩放当前图纸中的绘图视图。

映射是一组指令，用于定义：

* 几何体的最小和最大宽度。使用*表示匹配任何值
* 几何体的最小和最大高度。使用*表示匹配任何值
* 如果匹配，则缩放的分子和分母

几何尺寸是根据绘图视图中可见实体的边界框计算的（包括所有参考几何体、草图实体、尺寸和其他注释）：

![绘图视图几何尺寸参数](drawing-view-parameters.png){ width=350 }

所有绘图视图都有一个偏移边界。为了获得几何体的实际值，需要从视图尺寸中减去这个边界值。边界值是动态计算的（为图纸的宽度或高度的2%，取较小值）。这不是一个文档化的值，可能会在未来由SOLIDWORKS更改，这可能会影响到此宏中的计算。

![绘图视图的边界偏移](boundary-offset.png)

## 配置

### 范围

*BASE_VIEWS_ONLY* 变量控制是否应该缩放所有视图还是仅基本视图（即没有父视图的视图）。如果将此选项设置为 *True*，则会处理所有视图，并且派生视图将与原始源视图断开连接。

~~~
Const BASE_VIEWS_ONLY As Boolean = False '处理所有视图
~~~

### 缩放映射

在宏的开头配置缩放映射。根据需要指定多个映射条目。

~~~ vba
Dim scaleMap As Variant
scaleMap = Array("0-0.1;*;1:1", "0.1-0.2;0.05-0.1;1:2", "另一个条目", ..., "最后一个条目")
~~~

每个条目必须遵循预定义的格式：

~~~
"[最小宽度]-[最大宽度];[最小高度]-[最大高度];[缩放分子]:[缩放分母]"
~~~

* 宽度和高度的所有值都以米为单位
* 使用*表示允许任何宽度或高度

在下面的示例中

~~~ vba
Array("0-0.1;*;1:1", "0.1-0.2;0.05-0.1;1:2")
~~~

* 所有宽度最多为100毫米且任何高度的绘图视图将设置为1:1比例
* 所有宽度在100毫米到200毫米之间且高度在50毫米到100毫米之间的绘图视图将设置为1:2比例



{% code-snippet { file-name: Macro.vba } %}