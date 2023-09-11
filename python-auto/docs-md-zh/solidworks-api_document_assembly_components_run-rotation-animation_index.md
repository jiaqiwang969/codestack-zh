---
title: 使用SOLIDWORKS API运行组件的旋转动画
caption: 运行组件的旋转动画
description: 本示例演示了如何使用SOLIDWORKS API中的演示变换来运行组件围绕轴线的平滑旋转动画。
image: component-rotation.gif
labels: [装配, 变换, 旋转, 动画]
---
![组件围绕Y轴的旋转动画](component-rotation.gif)

此宏演示了如何使用演示变换通过[IComponent2::PresentationTransform](https://help.solidworks.com/2012/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.icomponent2~presentationtransform.html) SOLIDWORKS API方法来运行组件围绕其Y轴的平滑旋转动画。

这样可以仅为了视觉效果而移动组件，而不改变其几何形状。组件将被移动，无论它是否在空间中完全定义（通过约束或固定约束）。并且约束关系仍然保持不变。

* 选择装配中的任何组件并运行宏
* 组件将围绕其Y轴旋转
* 要停止动画，请取消选择（取消选择所有对象）
* 要修改旋转速度，请更改*RunRotationAnimation*方法的可选参数*speed*

~~~ vb
If Not swComp Is Nothing Then
    RunRotationAnimation swModel, swComp, 2 '速度x2
Else
    MsgBox "请选择组件"
End If
~~~

### 注意

为了启用演示模式，需要将[IAssemblyDoc::EnablePresentation](https://help.solidworks.com/2012/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.IAssemblyDoc~EnablePresentation.html)属性设置为True。

在动画完成后，需要将此属性设置为False，否则所有SOLIDWORKS菜单将被锁定：

![装配演示模式下的锁定菜单](locked-menu.png){ width=300 }

{% code-snippet { file-name: Macro.vba } %}