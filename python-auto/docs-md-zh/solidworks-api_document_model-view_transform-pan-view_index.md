---
标题：使用SOLIDWORKS API以屏幕像素为单位查看模型视图
说明：示例演示了如何通过提供屏幕像素的偏移量来平移模型视图
图片：pan-view.png
---
![模型视图平移](pan-view.png){ width=350 }

此示例演示了如何通过指定屏幕上的X和Y坐标的偏移量来移动视图（平移）。宏将偏移量转换为模型视图的3D空间，并更新视图位置。

{% code-snippet { file-name: Macro.vba } %}