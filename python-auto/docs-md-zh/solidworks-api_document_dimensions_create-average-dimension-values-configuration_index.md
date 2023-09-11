---
布局：sw-tool
标题：使用平均尺寸值创建SOLIDWORKS宏
说明：该宏将根据公差的最小值和最大值创建子配置，其中所有尺寸将被设置为平均值
图片：sw-dimension-tolerance.png
标签：[平均值，配置，尺寸，SOLIDWORKS API，公差，实用工具]
分组：模型
重定向自：
  - /2018/03/solidworks-api-dimensions-average-dims.html
---

该宏将使用SOLIDWORKS API创建子配置，其中所有尺寸将根据公差的最小值和最大值设置为平均值。

![属性管理器页面中的尺寸公差/精度组](sw-dimension-tolerance.png){ width=400 }

{% code-snippet { file-name: Macro.vba } %}