---
title: 使用SOLIDWORKS模型API创建挤出槽临时体
caption: 创建挤出槽临时体
description: 本示例演示了如何使用SOLIDWORKS API和IModeler接口将槽剖面挤出以创建临时体
image: extruded-slot.png
labels: [拓扑结构, 几何, 挤出, 槽]
---
![挤出槽剖面](extruded-slot.png){ width=250 }

这个VBA示例演示了如何通过挤出槽剖面来创建临时体。

宏将停止执行并在图形区域显示槽的预览。继续执行宏以隐藏预览并销毁临时体。

槽剖面是根据以下参数在*GetSlotProfileBody*函数中构建的：

![槽的参数](slot-parameters.png){ width=250 }

{% code-snippet { file-name: Macro.vba } %}