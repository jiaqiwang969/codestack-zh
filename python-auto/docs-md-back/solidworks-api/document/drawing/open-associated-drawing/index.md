---
layout: sw-tool
title: Open associated drawings of active document or selected components
caption: Open Associated Drawings
description: VBA macro to open the drawings associated to the component in its own window regardless of naming (with an option to open the drawing in detailing mode)
image: open-associated-drawing.svg
labels: [drawing, open, detailing]
group: Drawing
---
该VBA宏允许打开装配中选定组件的关联图纸，如果没有选定任何内容，则打开活动文档的关联图纸。

与原始功能不同，该宏没有与组件命名和位于同一文件夹的图纸相关的限制。该宏将在当前文件夹（活动文档的文件夹）的所有子文件夹中查找所有图纸，无论这些图纸是否以组件命名。

该宏有一个选项，可以以解析或详图模式打开图纸。修改**OPEN_DRAWING_DETAILING**的值以更改行为。

~~~ vb
Const OPEN_DRAWING_DETAILING As Boolean = True '以详图模式打开图纸
~~~

{% code-snippet { file-name: Macro.vba } %}