---
layout: sw-tool
title: SOLIDWORKS Macro to Split Body By Faces using SOLIDWORKS API
caption: Split Body By Faces
description: Macro splits the selected surface or solid body by faces creating individual sheet body for each face using SOLIDWORKS API
image: split-body-by-faces.svg
labels: [split,body,faces]
group: Geometry
---
![每个面的特征管理器树](feature-manager-tree-split-faces.png){ width=250 }

该宏使用[SOLIDWORKS API的IModeler::CreateSheetFromFaces](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.imodeler~createsheetfromfaces.html)方法，为选定的实体或曲面的每个面创建单独的曲面（平面）实体。

{% code-snippet { file-name: Macro.vba } %}

要了解更高级的功能（支持参数化方法），请参考[Geomtery++按面分割实体功能](/labs/solidworks/geometry-plus-plus/user-guide/split-body-by-faces/)。