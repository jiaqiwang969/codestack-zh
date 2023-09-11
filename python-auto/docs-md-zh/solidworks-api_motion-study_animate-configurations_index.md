---
layout: sw-tool
title: 使用SOLIDWORKS API制作宏动画切换配置
caption: 配置动画
description: 该宏演示了如何使用SOLIDWORKS API从配置中创建动画，以表示模型历史或折弯板金
image: animate-configurations.svg
labels: [运动, 动画, 折弯板金]
group: 运动研究
---
{% youtube { id: t35Kjjq509w } %}

该宏演示了如何使用SOLIDWORKS API从配置中创建动画。

当需要创建一个表示模型历史或折弯板金的动画时，这将非常有用。

* 打开零件或装配体
* 按照应该进行动画的顺序选择配置

![在配置选项卡中选择多个配置](sheet-metal-bending-animation.png){ width=350 }

* 运行宏。将创建一个新的装配体，并将配置设置为动画步骤。

![板金折弯动画](motion-study-configuration-animation.png){ width=450 }

宏参数（弯曲过渡时间和折叠操作之间的暂停时间）可以通过修改宏顶部的常量来进行更改

~~~ vb
Const TRANSITION_TIME As Double = 0.5
Const PAUSE_TIME As Double = 2
~~~

参考[在新配置中禁用特征](solidworks-api/document/features-manager/create-feature-configurations/)以获取一个从特征创建配置的宏。

{% code-snippet { file-name: Macro.vba } %}