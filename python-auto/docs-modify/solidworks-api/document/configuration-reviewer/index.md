---
title: VBA macro to review SOLIDWORKS sheets and configurations
caption: Configurations And Sheets Reviewer
description: VBA macro which iterates all sheets and configurations of SOLIDWORKS file and activates each one by one
image: configurations-reviewer.svg
labels: [configuration,sheet,review,iterate]
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