---
caption: Batch Create Folders
title: Batch create feature folders in the active SOLIDWORKS document
description: VBA macro creates specified number of the feature folders with the specified prefix name in the active SOLIDWORKS part or assembly
---
这个VBA宏允许在活动的SOLIDWORKS装配或零件文档中批量创建特征文件夹。

宏会询问要创建的文件夹数量和文件夹前缀名称。

宏会创建指定数量的文件夹，文件夹名称由前缀名称后跟索引组成。

> 如果下一个索引的文件夹已经存在，则使用下一个索引进行命名

{% code-snippet { file-name: Macro.vba } %}