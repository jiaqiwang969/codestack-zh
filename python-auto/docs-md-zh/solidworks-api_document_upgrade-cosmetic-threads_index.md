---
layout: sw-tool
title: 使用SOLIDWORKS API升级活动SOLIDWORKS零件或装配中的美化螺纹
caption: 升级美化螺纹
description: VBA宏升级美化螺纹为新版本（SOLIDWORKS 2020），以提高文档性能
image: upgrade-cosmetic-thread.png
labels: [api, 升级, 性能, 美化螺纹]
group: 性能
---
![升级美化螺纹命令](upgrade-cosmetic-thread.png){ width=500 }

此宏在SOLIDWORKS零件和装配中调用“升级美化螺纹特征”命令，可能会提高文档的性能。

此宏可与[SOLIDWORKS任务计划程序](https://help.solidworks.com/2019/English/SolidWorks/sldworks/c_SOLIDWORKS_Task_Scheduler_Overview.htm)或[Batch+](https://cadplus.xarial.com/batch/)等任务自动化软件一起使用。

{% code-snippet { file-name: Macro.vba } %}