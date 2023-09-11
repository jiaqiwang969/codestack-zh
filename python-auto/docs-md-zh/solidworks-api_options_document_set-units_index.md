---
caption: 设置文档单位
title: 设置SOLIDWORKS文档单位的宏（长度、角度、质量、体积、时间）
description: 用于设置SOLIDWORKS文档或自定义单位（长度、角度、质量、体积、时间）的VBA宏
image: document-units.png
---
![文档单位](document-units.png){ width=600 }

此宏允许更改活动的SOLIDWORKS文档（零件或装配体）的单位。

配置宏的常量以指定目标单位制

~~~ vb
Const UNIT_SYSTEM As Integer = swUnitSystem_e.swUnitSystem_Custom '根据下面的常量分别设置自定义单位

Const CUSTOM_LENGTH_UNIT As Integer = swLengthUnit_e.swMETER
Const CUSTOM_ANGLE_UNIT As Integer = swAngleUnit_e.swDEGREES
Const CUSTOM_MASS_UNIT As Integer = swUnitsMassPropMass_e.swUnitsMassPropMass_Pounds
Const CUSTOM_VOLUME_UNIT As Integer = swUnitsMassPropVolume_e.swUnitsMassPropVolume_Feet3
Const CUSTOM_TIME_UNIT As Integer = swUnitsTimeUnit_e.swUnitsTimeUnit_Second
~~~

如果**UNIT_SYSTEM**常量设置为**swUnitSystem_e.swUnitSystem_Custom**，则需要通过更改**CUSTOM_???**常量来提供每个自定义类型的单位。

{% code-snippet { file-name: Macro.vba } %}