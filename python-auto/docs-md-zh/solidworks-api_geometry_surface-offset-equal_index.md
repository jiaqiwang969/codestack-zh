---
layout: sw-tool
title: SOLIDWORKS VBA宏以复制预选面
caption: 复制曲面
description: SOLIDWORKS VBA宏通过调用“曲面偏移”功能并设置距离为0来复制所选面
image: surface-offset-equal.svg
labels: [曲面, 几何, 宏, 面, SOLIDWORKS API, VBA]
group: 几何
---
作者：[Eddy Alleman](https://www.linkedin.com/in/eddyalleman/) ([EDAL Solutions](www.edalsolutions.be))

![距离为0的偏移曲面](surface-offset-workflow.png){ width=525 }

此VBA宏在零件文件中从所选面创建一个新的曲面特征，从而复制所选曲面并给其指定的颜色。
如果您想重用现有曲面而不想合并现有曲面，则这将非常有用。

操作步骤

* 必须将零件文件设为活动文档。
* 您必须选择至少一个面。
* 如果选择其他类型的实体，它们将被过滤掉。
* 运行宏。结果将创建一个距离为0的曲面偏移特征。
* 默认情况下，此特征将呈黄色，但您可以更改RGB颜色以设置其他颜色。

作者：[Eddy Alleman](https://www.linkedin.com/in/eddyalleman/) ([EDAL Solutions](https://www.edalsolutions.be/index.php/en/))

{% code-snippet { file-name: Macro.vba } %}