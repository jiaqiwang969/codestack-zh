---
layout: sw-tool
title: SOLIDWORKS macro to create configuration with average dimension values
caption: Create Configuration With Average Dimension Values
description: Macro will create child configuration where all the dimension will be set to average value based on the minimum and maximum values of the tolerance
image: sw-dimension-tolerance.png
labels: [average, configuration, dimension, solidworks api, tolerance, utility]
group: Model
redirect-from:
  - /2018/03/solidworks-api-dimensions-average-dims.html
---

该宏将使用SOLIDWORKS API创建子配置，其中所有尺寸将根据公差的最小值和最大值设置为平均值。

![属性管理器页面中的尺寸公差/精度组](sw-dimension-tolerance.png){ width=400 }

{% code-snippet { file-name: Macro.vba } %}