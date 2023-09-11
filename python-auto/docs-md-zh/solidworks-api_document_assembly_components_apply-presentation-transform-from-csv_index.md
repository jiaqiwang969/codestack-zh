---
title: 使用SOLIDWORKS API从CSV文件加载组件展示变换
caption: 从CSV文件加载组件展示变换
description: 本示例演示了如何从CSV文件加载组件的变换矩阵，并将其应用为展示变换
image: original-component-position.png
labels: [装配, 变换, CSV]
---
![组件在原始位置](original-component-position.png){ width=250 }

本示例演示了如何使用SOLIDWORKS API从CSV文件加载组件的变换矩阵，并将其应用为展示变换。

* 下载并打开[示例SOLIDWORKS文件](presentation-transform-example.zip)
* 下载[CSV文件](transforms.csv)并保存到磁盘
* 修改宏常量中CSV文件的路径
* 运行宏。宏会停止执行，并将组件转换如下所示

![组件在变换后的位置](trasnsformed-component-position.png){ width=250 }

红色组件在XYZ空间中平移，绿色组件绕全局Y轴（轴1）旋转90度。

请注意，这些组件被移动，尽管它们都在空间中完全定义（通过配合或固定约束）。并且配合仍然保留。原因是应用了展示变换而不是永久变换。这允许仅为了视觉目的移动组件，而不改变几何形状。

按F5或播放按钮继续运行宏以移除展示变换。如果需要，可以使用[SOLIDWORKS API属性IComponent2::Transform2](https://help.solidworks.com/2012/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IComponent2~Transform2.html)来应用永久变换（在这种情况下，需要删除任何不适合此变换的配合）。