---
layout: sw-tool
title: 使用SOLIDWORKS API将实体按面分割的SOLIDWORKS宏
caption: 按面分割实体
description: 该宏使用SOLIDWORKS API将选定的曲面或实体按面分割，为每个面创建单独的平面实体
image: split-body-by-faces.svg
labels: [分割, 实体, 面]
group: 几何
---
![每个面的特征管理器树](feature-manager-tree-split-faces.png){ width=250 }

该宏使用[SOLIDWORKS API的IModeler::CreateSheetFromFaces](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.imodeler~createsheetfromfaces.html)方法，为选定的实体或曲面的每个面创建单独的曲面（平面）实体。

{% code-snippet { file-name: Macro.vba } %}

要了解更高级的功能（支持参数化方法），请参考[Geomtery++按面分割实体功能](/labs/solidworks/geometry-plus-plus/user-guide/split-body-by-faces/)。