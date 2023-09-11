---
layout: sw-tool
title: 使用SOLIDWORKS API从链接文件更新XYZ曲线的宏
caption: 从文件更新XYZ曲线
description: 使用VBA宏从链接的外部文本文件更新自由形式（通过XYZ点）曲线的坐标
image: curve.svg
labels: [曲线,链接,xyz,自由形式曲线]
group: 模型
---
![SOLIDWORKS特征管理器树中的自由形式曲线](feature-manager-xyz-curve.png){ width=450 }

SOLIDWORKS允许通过外部文本文件中的XYZ坐标插入自由形式曲线。然而，该文件并未链接到特征本身，当外部文件更改时，曲线也不会更新。

![从文件加载的曲线点](curve-file.png){ width=300 }

这个VBA宏可以自动将外部文件与坐标链接起来，并通过单击更新所选曲线。

曲线文件示例：

~~~
0mm 0mm 0mm
10mm 10mm 10mm
5mm 1mm 25mm
~~~

曲线文本文件必须保存在与SOLIDWORKS文件相同的文件夹中，并且必须命名为[模型标题]_[特征名称].sldcrv。例如，如果曲线特征命名为*Curve1*，并且位于名为Part1.sldprt的SOLIDWORKS文件中，则曲线文本文件必须命名为*Part1_Curve1.sldcrv*。

{% code-snippet { file-name: Macro.vba } %}