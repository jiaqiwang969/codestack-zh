---
layout: sw-tool
title: Macro to move suppressed mates into feature folder using SOLIDWORKS API
caption: Move Suppressed Mates Into A Folder
description: VBA macro to move suppressed mates in assembly into feature folder using SOLIDWORKS API
image: move-mates-to-folder.png
labels: [mates,suppressed,move,folder]
group: Assembly
---
![被压制的约束移动到文件夹中](suppressed-solidworks-mates.png){ width=250 }

这个VBA宏可以使用SOLIDWORKS API将所有被压制的约束移动到指定的特征管理器文件夹中。如果文件夹不存在，宏将创建一个新的文件夹，如果文件夹已经存在，则将移动到已存在的文件夹中。

如果文件夹中存在未被压制的约束，宏也会将它们一起移动。

要配置文件夹名称，请更改*FOLDER_NAME*变量的值：

~~~ vb
Const FOLDER_NAME As String = "<文件夹名称>"
~~~

{% code-snippet { file-name: Macro.vba } %}