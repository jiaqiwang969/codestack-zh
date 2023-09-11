---
title: 在SOLIDWORKS API中使用组件转换
caption: 组件转换在装配中
description: 本示例解释了装配中组件的旋转和平移转换
image: comp-translation.png
labels: [acos, 角度, 组件, 示例, 方向, 点, 位置, 旋转, SOLIDWORKS API, 转换, 平移, 向量]
redirect-from:
  - /2018/03/component-transformation-in-assembly.html
---

SOLIDWORKS组件是另一个父装配中模型（零件或装配）的实例。组件在其空间中的位置由其转换驱动（无论组件是否受到约束或通过自由拖放操作在空间中移动）。转换由三个组成部分组成：平移、旋转和缩放。

要获取组件的转换，请使用[SOLIDWORKS API属性IComponent2::Transform2](https://help.solidworks.com/2012/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.icomponent2~transform2.html)。在这种情况下，转换表示组件原点坐标系与根装配原点坐标系之间的关系。不需要将子装配的转换乘以其子组件的转换，以获得这些组件相对于根装配的总转换。

## 平移转换

在下面的示例中，组件在空间中沿X、Y和Z坐标移动。以下示例将计算组件原点的新位置：

![组件平移转换](comp-translation.png){ width=640 }

{% code-snippet { file-name: translation.vba } %}

运行此宏在[此示例模型](transform-translation.SLDASM)上将在监视窗口输出以下行作为结果：

> 沿X轴：75mm；沿Y轴：-50mm；沿Z轴：-100mm

## 旋转转换

现在让我们旋转组件并尝试找到旋转角度。该组件在所有方向上都被旋转。下面的**<span style="color: red;">红线</span>**是装配的X轴，**<span style="color: lime;">绿线</span>**是Y轴，**<span style="color: blue;">蓝线</span>**是Z轴。New X、New Y和New Z是组件中相应轴的方向，尺寸表示这些轴之间的角度。

![组件旋转转换](comp-rotation.png){ width=640 }

{% code-snippet { file-name: rotation.vba } %}

运行上述代码将输出以下结果，适用于[此示例模型](transform-rotation.SLDASM)：

> X轴之间的角度：110度

> Y轴之间的角度：66.74度

> Z轴之间的角度：75度

## 在配置中保留转换状态

默认情况下，浮动组件在配置中的转换状态将被装配修改的另一个配置状态覆盖，例如添加新组件、约束更改等。这与手动行为不同，当另一个配置修改时，浮动组件的位置不会改变。

为了演示这个问题，请考虑以下场景：

* 下载[示例装配](preserve-transform.zip)，其中有一个单独的组件
* 装配中有2个配置
  * 配置**A**通过约束完全定义了组件的位置
  * 配置**B**具有一个浮动组件，在随机位置上没有任何约束
* 运行以下宏。宏将使组件的角与装配的原点对齐在配置B中

![组件的角与装配的原点对齐](aligned-component.png)

* 宏将在几个点停止。阅读指示状态的注释
* 在最后一步中，浮动组件的转换被配置A中的由约束驱动的转换覆盖。

{% code-snippet { file-name: preserve.vba } %}

为了保留转换，需要在配置B中[固定](/solidworks-api/document/assembly/components/fix-float/)组件。

* 取消以下行的注释
* 关闭装配并重新打开

~~~ vb
'FixComponentInThisConfiguration swComp
~~~

改为

~~~ vb
FixComponentInThisConfiguration swComp
~~~

* 再次运行宏。现在转换被保留了