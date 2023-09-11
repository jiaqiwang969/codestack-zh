---
title: Get all external references of document using SOLIDWORKS Document Manager API
caption: Get All External References
description: Macro demonstrates how to extract all external references (including nested references) for specified SOLIDWORKS file using Document Manager API
labels: [document manager, external references, components]
---
该宏演示了如何使用SOLIDWORKS文档管理器API提取指定SOLIDWORKS文件（零件、装配或绘图）的所有外部引用，包括嵌套引用、装配组件和绘图视图。

修改宏并指定要收集引用的根文件的完整路径。

运行宏。所有引用将输出到即时窗口。

该宏使用[SOLIDWORKS文档管理器API的ISwDMDocument21::GetAllExternalReferences5](https://help.solidworks.com/2018/english/api/swdocmgrapi/SolidWorks.Interop.swdocumentmgr~SolidWorks.Interop.swdocumentmgr.ISwDMDocument21~GetAllExternalReferences5.html)方法列出文件的所有依赖项。该方法递归调用，以收集SOLIDWORKS装配的所有级别的引用。

{% code-snippet { file-name: Macro.vba } %}