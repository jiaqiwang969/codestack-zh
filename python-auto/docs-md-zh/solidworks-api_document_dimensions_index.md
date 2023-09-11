---
标题：使用SOLIDWORKS API处理尺寸
说明：通过SOLIDWORKS API自动化模型尺寸的文章和代码示例集合
顺序：7
图片：solidworks-dimensions-api.png
---

![通过SOLIDWORKS API自动化尺寸](solidworks-dimensions-api.png){ width=300 }

可以通过[SOLIDWORKS API的IModelDocExtension::AddDimension](https://help.solidworks.com/2022/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.imodeldocextension~adddimension.html)方法将尺寸添加到所选的草图段上。

每个尺寸都有一个用户可以分配的唯一名称。可以通过[IModelDoc2::Parameter](https://help.solidworks.com/2022/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.imodeldoc2~parameter.html)方法按名称检索尺寸对象。

请参考[SOLIDWORKS API接口IDimension](https://help.solidworks.com/2022/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IDimension.html)以获取可用于尺寸自动化的方法列表。