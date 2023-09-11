---
layout: sw-tool
title: Upgrade cosmetic threads in active SOLIDWORKS part or assembly using SOLIDWORKS API
caption: Upgrade Cosmetic Threads
description: VBA macro upgrades cosmetic threads to a new (SOLIDWORKS 2020) version which allows to improve performance of the document
image: upgrade-cosmetic-thread.png
labels: [api, upgrade, performance, cosmetic thread]
group: Performance
---
![升级美化螺纹命令](upgrade-cosmetic-thread.png){ width=500 }

此宏在SOLIDWORKS零件和装配中调用“升级美化螺纹特征”命令，可能会提高文档的性能。

此宏可与[SOLIDWORKS任务计划程序](https://help.solidworks.com/2019/English/SolidWorks/sldworks/c_SOLIDWORKS_Task_Scheduler_Overview.htm)或[Batch+](https://cadplus.xarial.com/batch/)等任务自动化软件一起使用。

{% code-snippet { file-name: Macro.vba } %}