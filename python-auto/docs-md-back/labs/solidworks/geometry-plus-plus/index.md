---
title: Geometry++ - add-in which complements SOLIDWORKS geometry commands
caption: Geometry++
description: SOLIDWORKS add-in providing additional set of commands related to geometry modifications and creation
image: logo.png
categories: sw-labs
group: Geometry
toc-group-name: labs-solidworks-geometry-plus-plus
type: sw-lab
---
![几何++](logo.png)

几何++是一个SOLIDWORKS插件，扩展了与几何创建和操作相关的功能。该插件完全集成到SOLIDWORKS中，并提供与任何其他内置功能相同的附加功能的外观和感觉。所有功能都保留参数化行为，并在需要时自动重新生成。

有关更多信息和下载链接，请参阅[安装](installation)页面。

源代码可在[GitHub](https://github.com/codestackdev/geometry-plus-plus)上获得。

## 功能

### 将实体转换为曲面

![将实体转换为曲面](/labs/solidworks/geometry-plus-plus/user-guide/convert-solid-to-surface/icon.png)

此命令将实体转换为曲面。可以在一个特征中转换多个输入实体。

### 裁剪实体

![裁剪实体](/labs/solidworks/geometry-plus-plus/user-guide/crop-bodies/icon.png)

此命令允许使用草图或草图区域（修剪工具）裁剪曲面和实体（目标实体）。

### 带帽子的曲面挤压

![带帽子的曲面挤压](/labs/solidworks/geometry-plus-plus/user-guide/extrude-surface-cap/icon.png)

此命令允许挤压曲面并在挤压的两端添加帽子。

### 实体倒角

![实体倒角](/labs/solidworks/geometry-plus-plus/user-guide/body-fillet/icon.png)

此命令允许在整个实体、面、边和顶点上添加倒角，支持在单个特征中处理多个实体。

### 按面分割实体

![按面分割实体](/labs/solidworks/geometry-plus-plus/user-guide/split-body-by-faces/icon.png)

此命令允许从输入的实体或曲面实体的所有面创建曲面（片段）实体。

## 性能

![暂停重建](/labs/solidworks/geometry-plus-plus/user-guide/suspend-rebuild/icon.png)

此命令允许在SOLIDWORKS零件、装配和绘图中临时暂停重建操作，以将多个重建操作合并为一个操作，以减少重建时间。