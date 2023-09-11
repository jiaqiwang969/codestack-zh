标题：使用SOLIDWORKS API将线条与轴对齐
标题：将线条与轴对齐
描述：示例演示了如何使用SOLIDWORKS API将活动草图中的所有草图线条（添加草图关系）与所选选项之一（沿X、Y或Z轴）对齐。
图片：sw-sketch-line-relation.png
标签：[示例，水平，关系，草图，solidworks api，垂直]
重定向自：
  - /2018/03/solidworks-api-sketch-align-line-relations.html
---

示例演示了如何使用SOLIDWORKS API将活动草图中的所有草图线条（添加草图关系）与所选选项之一对齐：

* 沿X轴（水平）
* 沿Y轴（垂直）
* 沿Z轴

此示例适用于2D和3D草图。

使用[ISketchRelationManager](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isketchrelationmanager.html) SOLIDWORKS API接口来管理草图实体的关系。

![草图线条中的关系](sw-sketch-line-relation.png){ width=320 height=229 }

{% code-snippet { file-name: Macro.vba } %}