---
layout: sw-tool
title: 在SOLIDWORKS模型中添加水印的宏功能
caption: 添加水印功能
description: 添加水印功能（许可证），包括自定义信息和名称，无法被删除或编辑
image: model-watermark.png
labels: [安全, 宏功能, 锁定]
group: 安全
---
{% youtube { id: v-S2idKXWDY } %}

本文将介绍如何使用SOLIDWORKS API在任何模型中嵌入水印功能，以保护知识产权或指示该模型在特殊条件下使用。如果需要将许可证嵌入到无法被第三方编辑的模型中，这将非常有用。

插入的功能无法通过用户界面或API删除、抑制、移除或更改。

该功能可以插入到任何SOLIDWORKS模型（零件、文档、绘图或模板）中。

该功能完全嵌入到模型中。

解决方案由两部分组成：

* 制作宏。用于插入水印。此宏不会嵌入到模型中。
* 水印宏。此宏表示水印功能，并将直接嵌入到模型中。

## 设置制作宏

* 在SOLIDWORKS中创建新的宏（从SOLIDWORKS菜单中选择“工具”->“宏”->“新建...”命令）
* 指定要保存此文件的名称
* 将以下代码复制到宏中

{% code-snippet { file-name: InsertWatermark.vba } %}

为了添加自定义图标，请下载[图标](Icons.zip)文件并解压缩到与宏功能文件相邻的**Icons**子文件夹中

## 设置水印宏

* 创建另一个新的宏
* 将此宏的名称指定为*Watermark.swp*，并将其保存到与前面的制作宏相同的文件夹中

> 如果使用不同的名称，则需要修改制作宏中的以下常量的名称

~~~ vb
Const WATERMARK_MACRO_NAME = "Watermark.swp"
~~~

* 将常量中的安全提示更改为只读的不可修改的提示。

~~~ vb
Const SECURITY_NOTE = "www.codestack.net"
~~~

* 将以下代码复制到宏中

{% code-snippet { file-name: Watermark.vba } %}

### 修改参数

宏中有几个参数可以进行修改，这些参数在宏的顶部被定义为常量

~~~ vb
Const MESSAGE As String = "Watermark Feature by CodeStack"
Const FEATURE_NAME As String = "www.codestack.net"
~~~

* *MESSAGE* 是用户编辑水印功能时显示的自定义消息
* *FEATURE_NAME* 是特征管理器树中水印功能的名称

### 设置宏密码

为水印宏分配密码，以防止用户更改。

* 从水印宏的上下文菜单中选择“属性”命令

![VBA宏上下文菜单中的属性命令](vba-macro-properties.png){ width=200 }

* 选择“保护”选项卡
* 选中“锁定项目以供查看”选项
* 在密码框中指定密码

![VBA宏保护选项卡](vba-macro-protection.png){ width=250 }

* 保存宏并关闭

## 插入水印

* 要插入水印，只需打开模型并运行[制作宏](#设置制作宏)
* 保存模型

## 水印行为

* 水印功能将始终移动到特征树的底部
* 当编辑水印功能的定义时

![调用编辑水印功能的定义](vba-edit-watermark-feature.png){ width=250 }

将显示自定义消息

![编辑水印功能时显示的自定义消息框](watermark-messagebox.png){ width=250 }

* 在尝试删除该功能时，将显示以下消息

![无法删除水印](watermark-cannot-be-deleted.png){ width=250 }

* 在模型原点处添加了不可编辑的安全提示

![不可编辑的安全水印提示](watermark-security-note.png){ width=250 }

* 功能名称无法更改。可以对其重命名，但在状态更新（例如选择、重建、打开模型等）时，名称将被恢复。