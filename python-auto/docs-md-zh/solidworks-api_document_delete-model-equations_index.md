---
layout: sw-tool
title: 使用SOLIDWORKS API从SOLIDWORKS模型中删除所有方程式
caption: 删除所有方程式
description: 该宏可以使用SOLIDWORKS API从活动模型（零件或装配）中删除所有方程式（或仅删除损坏的方程式）。
image: deleted-equations.svg
labels: [api, 清理, 删除方程式, 方程式, 宏, 实用工具, vba]
group: 模型
redirect-from:
  - /2018/03/delete-all-equations-from-solidworks.html
---

该宏可以使用SOLIDWORKS API从活动模型（零件或装配）中删除所有方程式（或仅删除损坏的方程式）。

![方程式管理器对话框](equations-manager.png){ width=640 }

如果活动模型是装配体，则该宏还可以选择删除装配体中每个组件的所有方程式。将显示以下消息。点击**是**以删除所有级别上的所有组件的方程式，点击**否**仅处理顶层装配体的方程式。

![宏选项以删除装配体组件中的方程式](delete-comps.png){ width=320 height=120 }

将*DELETE_BROKEN_ONLY*选项设置为*True*，以仅删除损坏（悬挂）的方程式。

**重要提示：请自行承担使用此宏的风险。该宏会修改您的数据（删除所有方程式），请在运行此宏之前备份您的文件**

{% code-snippet { file-name: Macro.vba } %}