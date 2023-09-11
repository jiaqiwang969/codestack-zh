---
layout: sw-tool
title: 使用VBA宏将展开图视图重命名为切割清单名称
caption: 使用切割清单名称重命名展开图视图
description: 使用SOLIDWORKS API，使用VBA宏将活动工作表中的所有展开图视图重命名为相应的切割清单名称
image: 重命名的展开图绘图视图.png
labels: [重命名视图,切割清单,展开图]
group: 绘图
---
![钣金零件的切割清单](切割清单名称.png){ width=250 }

钣金零件的切割清单名称可用于存储重要信息，例如零件编号。此VBA宏允许使用SOLIDWORKS API将活动绘图工作表中的所有钣金展开图视图重命名为相应的切割清单项名称。

![绘图视图重命名为切割清单后](重命名的展开图绘图视图.png){ width=250 }

{% code-snippet { file-name: Macro.vba } %}