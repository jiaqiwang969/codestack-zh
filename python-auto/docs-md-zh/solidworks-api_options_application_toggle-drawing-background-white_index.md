---
layout: sw-tool
title: VBA宏切换绘图的白色背景
caption: 切换绘图的白色背景
description: 使用系统设置的VBA宏，切换绘图的白色背景为您选择的其他颜色
image: ToggleWhiteBackground-icon.svg
labels: [绘图, 选项, 背景, 截图]
group: 选项
---
作者：[Eddy Alleman](https://www.linkedin.com/in/eddyalleman/) ([EDAL Solutions](https://www.edalsolutions.be/index.php/en/))

![手动设置SolidWorks绘图背景的系统选项](solidworks-option-background.png){ width=450 }

介绍
在SolidWorks论坛上，有人问如何制作一个宏，可以在默认绘图背景颜色和白色之间切换。
目标是使捕捉需要白色背景的图像更加容易。

这是一个简单的宏，可以实现这个目标。我还会解释您需要的基本按钮/快捷键/菜单。

如果您想在其他颜色之间切换，可以在下面的Color1和Color2常量中进行更改。

## 但是我们如何得到与我们想要的颜色对应的数字呢？
只需在SolidWorks选项中手动更改为您喜欢的颜色（在上面的图像中，我选择了一种更加鲜明的黄色）
然后使用宏编辑器打开宏（菜单工具 > 宏 > 编辑，或使用宏工具栏）。
如果立即窗口尚未可见，请打开它（CTRL + G）
运行宏（F5或绿色箭头按钮），在立即窗口中，您应该看到您选择的颜色用一个数字表示：

![运行宏后立即窗口显示选择的颜色](vba-immediate-window-chosen-color.png)

在代码中调整数字（Color2），当您运行宏时，背景颜色将在白色和您喜欢的颜色之间切换。

{% code-snippet { file-name: Macro.vba } %}