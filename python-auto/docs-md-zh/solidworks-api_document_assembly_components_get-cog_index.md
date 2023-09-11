获取SOLIDWORKS组件在装配中的重心
获取重心
这个宏演示了两种方法来计算SOLIDWORKS装配空间中组件的重心（COG）。

宏将计算所选组件的重心。

## 坐标转换

[IModelDocExtension::GetMassProperties2](https://help.solidworks.com/2017/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IModelDocExtension~GetMassProperties2.html) API允许计算模型中的质量属性数据。

当在组件的模型级别上计算时，需要使用变换将坐标转换为装配空间，以获得所需的结果。

{% code-snippet { file-name: MacroTransform.vba } %}

## 使用IMassProperty接口

[IMassProperty](https://help.solidworks.com/2017/English/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.IMassProperty.html)接口模拟了SOLIDWORKS中的质量属性功能

![质量属性对话框](mass-property.png){ width=400 }

与UI等效物类似，可以为计算范围分配实体（包括组件实体）。

与之前的方法相比，这种方法的主要优点之一是可以计算轻量级组件的重心。

{% code-snippet { file-name: MacroMassPrp.vba } %}