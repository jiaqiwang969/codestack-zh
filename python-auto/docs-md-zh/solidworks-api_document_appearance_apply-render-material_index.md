---
caption: 应用渲染材料;
title: 使用SOLIDWORKS API生成材料变体配置
description: 使用VBA宏生成一系列具有自定义外观的配置
image: configurations.png
---
![生成的配置](configurations.png)

这个VBA宏将生成一系列与模型的材料变体相对应的配置。

宏将根据文件名和指定的后缀为配置分配名称。

宏将创建一个配置特定的属性，该属性基于文件特定的属性和颜色的名称。

宏不会生成新的显示状态，并假设选择了“将显示状态链接到配置颜色”选项，因此显示状态附加到配置。

![将显示状态链接到配置颜色](link-display-states-configuration.png)

## 配置

指定要创建的属性的名称

~~~ vb
Const PRP_NAME As String = "描述"
~~~

通过修改**CONFIGS_DATA**数组来配置配置的输入参数

将数组的大小设置为总实例数减1，例如5个实例的情况下为4，1个实例的情况下为0

~~~ vb
Dim CONFIGS_DATA(0) As ConfigData

CONFIGS_DATA(0).colorName = "我的颜色"
CONFIGS_DATA(0).ConfigNameSuffix = "-9"
CONFIGS_DATA(0).MaterialFilePath = "D:\my-color.p2m"
~~~

* colorName - 要写入自定义属性的颜色名称后缀
* ConfigNameSuffix - 配置的后缀名称，可以为空（在这种情况下，配置将以文件名命名）
* MaterialFilePath - 应用的外观的*.p2m*文件的完整路径。如果为空，则保留当前外观

宏将为从第二个开始的所有实例创建新的配置。第一个实例将被跳过，并且活动配置将用于该过程（例如重命名和上色）。

{% code-snippet { file-name: Macro.vba } %}