---
标题：使用SOLIDWORKS API创建垂直于屏幕视图的向量
说明：示例演示了如何使用SOLIDWORKS API绘制与屏幕相对于当前视图方向垂直（正交）的草图线。
图片：sw-view-screen-transformation.png
标签：[示例，垂直，屏幕，SOLIDWORKS API，转换，视图]
重定向自：
  - /2018/04/solidworks-api-transformation-create-vector-normal-to-screen-view.html
---

这个示例演示了如何使用SOLIDWORKS API绘制与屏幕相对于当前视图方向垂直（正交）的草图线。

该线将从屏幕中间的点开始，并且垂直于屏幕方向。这意味着最初它将被渲染为一个点，直到视图旋转。

使用[SOLIDWORKS API的IModelView::Transform](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.imodelview~transform.html)属性来提取当前视图方向的转换矩阵。

![与当前图形视图垂直的线条](sw-view-screen-transformation.png){ width=320 height=208 }

{% code-snippet { file-name: Macro.vba } %}