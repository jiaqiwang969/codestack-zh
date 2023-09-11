---
title: Create extruded slot temp body using SOLIDWORKS modeler API
caption: Create Extruded Slot Temp Body
description: Example demonstrates how to extrude the slot profile to create a temp body using SOLIDWORKS API and IModeler interface
image: extruded-slot.png
labels: [topology, geometry, extrude, slot]
---
![挤出槽剖面](extruded-slot.png){ width=250 }

这个VBA示例演示了如何通过挤出槽剖面来创建临时体。

宏将停止执行并在图形区域显示槽的预览。继续执行宏以隐藏预览并销毁临时体。

槽剖面是根据以下参数在*GetSlotProfileBody*函数中构建的：

![槽的参数](slot-parameters.png){ width=250 }

{% code-snippet { file-name: Macro.vba } %}