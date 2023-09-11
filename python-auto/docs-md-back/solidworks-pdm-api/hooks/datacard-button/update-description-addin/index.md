---
title: Concatenate description variable on a data card button click using SOLIDWORKS PDM API
caption: Concatenate Description Variable
description: This example demonstrates how to handle the button click on data card and concatenate value of description variable based on values of revision and number variables in PDM add-in using SOLIDWORKS PDM Professional API
image: button-update-variable.gif
labels: [hook, button click, variables]
---
本示例演示了如何使用SOLIDWORKS PDM API在数据卡上处理按钮点击，并根据PDM附加组件中修订号和编号变量的值连接描述变量。

* 在PDM管理控制台中向数据卡添加按钮
* 将*命令类型*选项设置为*运行附加组件*
* 指定附加组件的名称，如下图所示。此选项允许指定唯一标签，当按钮被点击时，附加组件可以通过此标签正确识别按钮。

![数据卡设置选项](data-card-button.png){ width=500 }

此选项应与附加组件中的*BUTTON_TAG*常量的值相等。

~~~ cs
private const string BUTTON_TAG = "_UpdateDesc_";
~~~

* 确保数据卡上存在*编号*、*修订号*和*描述*变量，或根据需要修改附加组件代码：

当按钮被点击时，*描述*变量将根据*编号*和*修订号*变量的值连接更新。

![按钮点击时更新描述](button-update-variable.gif){ width=450 }

{% code-snippet { file-name: add-in.cs } %}