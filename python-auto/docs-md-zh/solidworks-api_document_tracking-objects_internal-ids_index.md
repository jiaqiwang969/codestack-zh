---
title: 使用SOLIDWORKS API中的内部ID
caption: 内部ID
description: 本文介绍了内部ID的使用方法以及从对象中读取ID的方式
image: sketch-segments-ids.png
labels: [ID, 追踪, 内部ID]
---
![分配给草图线的内部ID](sketch-segments-ids.png){ width=350 }

内部ID通常是整数或长整数值，用于在模型中唯一标识SOLIDWORKS对象。ID是持久的，在重建操作或会话之间不会改变。当对象发生更改时（例如，特征重命名或草图线更改坐标），ID也会更新。

> 草图元素（点、线段、填充）由2个整数或长整数ID组成

与[持久引用ID](solidworks-api/document/tracking-objects/persist-references)一样，内部ID不能更改或分配，并且在GUI中不可见（例如，仅在API中可用）。但与持久引用ID不同的是，无法通过内部ID查找对象，即需要遍历所有对象才能通过ID找到所需对象。

如果需要索引所有元素（例如草图线段或特征）并尽量减小索引数据的大小（例如，如果需要将数据存储在第三方存储中或通过网络发送），则应使用内部ID。

可以为以下对象访问内部ID：

* 零件
* 配置
* 特征
* 图层
* 光源
* 工作表
* 草图填充
* 草图点
* 草图线段

以下示例演示了如何使用SOLIDWORKS API从所选对象中检索内部ID。返回的ID数组还包含ElementType_e枚举器中定义的对象类型。

{% code-snippet { file-name: Macro.vba } %}