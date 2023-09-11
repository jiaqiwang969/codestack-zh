---
layout: sw-tool
title: Macro to close all SOLIDWORKS documents except active
caption: Close All Documents Except Active
description: Closes all opened documents except of an active one using SOLIDWORKS API
image: close-all-but-active.svg
labels: [close, window]
group: Frame
---
![在SOLIDWORKS中打开的文档](opened-documents.png){ width=250 }

此宏利用SOLIDWORKS API关闭除活动文档外的所有已打开文档。

如果文档有未保存的更改（即脏文档），宏将提示用户为要关闭的文档指定操作（保存、不保存或取消）。否则，文档将被静默关闭。

观看[视频演示](https://youtu.be/9uZCecGg25I?t=166)

{% code-snippet { file-name: Macro.vba } %}