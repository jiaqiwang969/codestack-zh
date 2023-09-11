---
caption: 射线交点
title: 通过射线交点在SOLIDWORKS模型中找到交点和拓扑实体
description: 使用VBA宏在SOLIDWORKS零件文档中找到交点和相应的拓扑实体，使用从所选草图的草图点创建的射线
image: ray-intersection-entities.png
---
这个VBA宏示例演示了如何在活动的SOLIDWORKS零件文档的所有实体之间以及从所选草图的草图点创建的射线之间找到交点和相应的拓扑实体。

## 如何运行宏

* 打开或创建一个带有可见实体的零件文档。
* 创建2D草图并添加草图点。草图点将用作射线的起始点。草图法线将用作射线的方向。
* 选择上述草图。
* 运行宏。宏将找到所有的交点并在每个找到的结果上暂停。
    * 宏将将每个射线的信息输出到[VBA即时窗口](/visual-basic/vba/vba-editor/windows#immediate-window)中。信息包括实体的名称、射线信息（起始点和方向）以及交点类型，交点类型定义在[swRayPtsResults_e](https://help.solidworks.com/2020/english/api/swconst/SolidWorks.Interop.swconst~SolidWorks.Interop.swconst.swRayPtsResults_e.html)中。
    
    ![射线交点信息](ray-intersection-result.png)

    * 宏将选择射线所击中的相应实体（面或边）。选择点将指示射线击中实体的位置。
    * 使用F5或VBA编辑器中的**运行**按钮继续执行宏以遍历所有结果。

    ![射线交点实体](ray-intersection-entities.png)

{% code-snippet { file-name: Macro.vba } %}