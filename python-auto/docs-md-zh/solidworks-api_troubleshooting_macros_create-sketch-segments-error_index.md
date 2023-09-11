---
layout: sw-macro-fix
title: 修复使用SOLIDWORKS API创建草图段时的错误
caption: 创建草图段失败
description: 修复宏中草图段（线段、弧线等）或草图点创建的不一致性
labels: [宏, 故障排除]
redirect-from:
  - /2018/04/宏故障排除-创建草图段失败.html
---
## 症状

SOLIDWORKS宏使用SOLIDWORKS API创建草图段（线段、弧线等）或草图点。在某些情况下，这些元素无法创建，而在其他情况下可以正常工作。

## 原因

默认情况下，使用[ISketchManager](https://help.solidworks.com/2016/English/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.ISketchManager.html)接口插入的所有实体都是通过用户界面创建的。这意味着如果目标区域（即段的边界）在用户界面中不可见（例如视图被移动或缩放），则无法创建实体。

## 解决方法

在创建实体之前将[ISketchManager::AddToDB](https://help.solidworks.com/2016/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isketchmanager~addtodb.html)属性设置为*True*，并在任务完成后恢复原始值。
将此选项设置为true将绕过通过用户界面创建实体，而是直接将数据添加到模型存储中。这也可以提高创建实体的性能。

{% code-snippet { file-name: add-to-db.vba } %}