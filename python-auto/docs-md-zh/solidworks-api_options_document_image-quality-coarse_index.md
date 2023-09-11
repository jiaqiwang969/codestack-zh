---
layout: sw-tool
title: 使用SOLIDWORKS API在用户首选项中设置活动文档的ShadedImageQualityCoarse
caption: 将阴影图像质量设置为粗糙
description: SolidWorks VBA宏，用于在零件和装配文件中将阴影图像质量设置为粗糙。如果活动文档是装配体，则还将设置“应用于所有引用的零件文档”的复选标记为打开状态。
image: coarse-icon.svg
labels: [文档, 首选项, 选项, 图像质量, 批处理+]
group: 选项
---
作者：[Eddy Alleman](https://www.linkedin.com/in/eddyalleman/) ([EDAL Solutions](www.edalsolutions.be))

![将阴影图像质量设置为粗糙](Image-Quality-Coarse.png){ width=650 }

在处理大型装配体时，您可以设置文档选项，以便将文件保存得尽可能轻量：

## 阴影和草图质量HLR/HLV分辨率
控制用于阴影渲染输出的曲面细分。较高的分辨率设置会导致模型重建速度变慢，但曲线更准确。
低（较快）- 高（较慢）

这意味着，如果您在装配体中工作，可以手动将所有引用的文件设置为低图像质量。

但是，如果您有很多文件并且需要在大型装配体中工作，可以使用宏在打开根装配体之前帮助使文件变得更轻。

此宏设置了上述图像中显示的两个选项（1）和（2）。零件无法使用选项（2）。

如果您将此宏与Batch+一起使用，其真正的威力就会显现出来。您可以在不处理装配体时运行它。

![示例设置，让Batch+在后台运行并处理文件的保存](batch-plus-settings.png){ width=800 }

{% code-snippet { file-name: Macro.vba } %}