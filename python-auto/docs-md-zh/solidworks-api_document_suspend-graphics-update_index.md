---
title: 使用SOLIDWORKS API挂起图形更新的宏
caption: 挂起图形更新
description: 本示例演示了如何在使用SOLIDWORKS API执行操作时抑制图形更新。
labels: [api, 图形, 实用工具, 挂起, 性能]
---
该宏演示了如何在使用特征树和模型（包括打开新文档）进行操作时挂起图形更新，使用SOLIDWORKS API。

该宏将外部零件中的实体复制到活动零件文档的新创建的派生配置中。

通过 *SRC_PART* 常量设置源零件路径（要复制实体的零件）。

~~~ vb
Const SRC_PART As String = "C:\Sample.sldprt"
~~~

通过更改 *SUPPRESS_UPDATES* 常量来尝试两种选项以查看差异。

~~~ vb
Const SUPPRESS_UPDATES As Boolean = True 'True表示抑制更新，False表示显示更新（默认行为）
~~~

该宏执行以下步骤：

* 打开要复制实体的模型
* 将所有实体复制到内存中
* 关闭模型
* 在原始模型中创建新的派生配置
* 插入复制的实体
* 在除此配置之外的所有配置中抑制创建的特征
* 激活原始配置

如果将 *SUPPRESS_UPDATES* 选项设置为true，则所有操作将被隐藏，屏幕上只会显示模型的活动状态（即模型打开、特征插入等将不可见）。

{% code-snippet { file-name: Macro.vba } %}