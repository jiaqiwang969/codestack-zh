---
caption: Split Folders To Configurations
title: Split feature folders of the SOLIDWORKS file to individual configurations
description: VBA macro creates individual configurations for each feature folder in the active SOLIDWORKS part or assembly
---
此VBA宏为活动的SOLIDWORKS零件或装配中的每个顶级功能文件夹创建配置。

如果模型中没有选择任何对象，则将处理所有文件夹功能，否则只处理所选的功能文件夹。

创建的配置将以功能文件夹的名称命名。

可以指定为每个功能文件夹创建派生配置还是顶级配置。

~~~ vb
Const CREATE_DERIVED_CONFS As Boolean = True 'True表示创建派生配置，False表示创建顶级配置
~~~

每个配置都将禁用所有其他文件夹。文件夹外的功能将不会被禁用。

{% code-snippet { file-name: Macro.vba } %}