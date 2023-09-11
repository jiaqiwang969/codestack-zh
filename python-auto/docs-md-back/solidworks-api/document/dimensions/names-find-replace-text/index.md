---
layout: sw-tool
title: Find-replace text in dimension names using SOLIDWORKS API
caption: Find-Replace Text In Dimension Names
description: Macro replaces the text in the dimension names of the selected feature or features
image: rename-dims.png
labels: [dimension, example, find, model, rename, replace, solidworks, solidworks api]
group: Model
redirect-from:
  - /2018/03/find-replace-text-in-dimension-names.html
---
该宏可以使用SOLIDWORKS API在所选特征的尺寸名称中查找和替换文本（类似于文本编辑器中的查找和替换功能）：

![在尺寸名称中查找文本的输入框](rename-dims.png){ width=320 }

1. 打开SOLIDWORKS装配或零件
2. 选择要查找尺寸的特征
3. 运行宏
4. 指定要查找的文本和要替换的文本。只包括短尺寸名称。
例如，Sketch1中的尺寸D1将具有短名称*D1*和完整名称*D1@Sketch1*。在查找字段中指定*D*，在替换字段中指定*B*，将导致尺寸重命名为*B1@Sketch1*。

{% code-snippet { file-name: Macro.vba } %}