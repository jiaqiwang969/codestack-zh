---
标题：使用SOLIDWORKS API操纵模型视图
说明：收集有关使用SOLIDWORKS API处理3D模型视图的文章和代码示例
顺序：3
---
模型视图是SOLIDWORKS模型在用户界面上可见的3D快照。SOLIDWORKS API提供了[IModelView](https://help.solidworks.com/2018/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IModelView.html)接口，用于对视图进行操作和数据提取。

可以对模型视图进行变换（缩放、旋转、移动），以改变模型的方向。

文档中可以呈现多个视图，以表示模型的不同状态。例如，运动研究选项卡会创建新的视图，以渲染与运动相关的用户界面元素。

本节包含使用SOLIDWORKS API操纵模型视图的示例和宏。