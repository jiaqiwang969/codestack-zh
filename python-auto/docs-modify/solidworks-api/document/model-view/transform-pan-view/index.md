---
title: Pan model views with screen pixels using SOLIDWORKS API
caption: Pan Model View
description: Example demonstrates how to pan a model view with view transforms by providing the offset in the screen pixels
image: pan-view.png
---
![模型视图平移](pan-view.png){ width=350 }

此示例演示了如何通过指定屏幕上的X和Y坐标的偏移量来移动视图（平移）。宏将偏移量转换为模型视图的3D空间，并更新视图位置。

{% code-snippet { file-name: Macro.vba } %}