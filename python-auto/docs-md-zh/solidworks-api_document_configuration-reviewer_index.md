---
title: VBA宏以审查SOLIDWORKS工作表和配置
caption: 配置和工作表审查者
description: VBA宏，用于迭代SOLIDWORKS文件的所有工作表和配置，并逐个激活它们
image: configurations-reviewer.svg
labels: [配置,工作表,审查,迭代]
---
![SOLIDWORKS模型中的配置](configurations.png)

此VBA宏允许审查SOLIDWORKS零件或装配体中的所有配置以及绘图文档中的所有工作表。

宏将逐个激活每个工作表或配置，并在激活下一个配置之前等待指定的秒数。

通过更改*WAIT_TIME*常量的值来指定在激活下一个配置或工作表之前等待的秒数。

~~~vb
Const WAIT_TIME As Single = 10 ' 在激活下一个配置或工作表之前等待10秒
~~~

主窗口不会被阻塞，因此可以在图形视图中操作模型。

{% code-snippet { file-name: Macro.vba } %}