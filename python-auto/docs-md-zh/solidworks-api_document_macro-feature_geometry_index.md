---
title: 使用SOLIDWORKS API生成盒子几何体（实体、表面、线框）宏特征
caption: 生成盒子几何体
description: 使用SOLIDWORKS API创建VBA宏特征的示例，可以生成不同类型的盒子几何体（实体、表面、线框）
image: solid-body.png
labels: [宏特征, 几何体, 盒子, 实体, 表面, 线框]
---
这个VBA示例演示了如何创建生成自定义几何体的宏特征。

打开零件文档并运行宏。新的特征将被插入到特征管理器树中，并且会生成实体、表面或线框几何体。

## 配置

### 嵌入

将*EMBED_MACRO_FEATURE*常量的值设置为指定是否将宏特征嵌入到文件中。如果将此选项设置为*True*，则可以在任何其他计算机上打开零件文档，而无需复制宏即可查看几何体。

### 盒子尺寸

可以通过更改*WIDTH*、*LENGTH*和*HEIGHT*常量来配置盒子的尺寸：

~~~ vb
Const WIDTH As Double = 0.01
Const LENGTH As Double = 0.01
Const HEIGHT As Double = 0.01
~~~

### 几何体类型

可以通过将值分配给*BODY_TYPE*常量来设置生成的几何体类型。

#### swBodyType_e.swSolidBody

创建一个实体几何体的盒子。

![宏特征生成实体几何体](solid-body.png){ width=350 }

#### swBodyType_e.swSheetBody

通过缝合盒子的面创建一个单一表面几何体。

![宏特征生成表面（sheet）几何体](surface-body.png){ width=350 }

#### swBodyType_e.swWireBody

从盒子几何体的所有边创建线框几何体。线框几何体是边界，不会出现在几何体文件夹中。标准特征树中使用的线框几何体的示例是曲线（复合、通过XYZ、投影等）。

![宏特征生成线框几何体](wire-body.png){ width=350 }

{% code-snippet { file-name: Macro.vba } %}