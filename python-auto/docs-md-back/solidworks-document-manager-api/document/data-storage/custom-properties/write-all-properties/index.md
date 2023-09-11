---
title: Write custom properties to all sources using Document Manager API
caption: Write All Properties
description: VBA macro to write custom properties to all sources (file, configuration, cut-list items) using Document Manager API
image: added-custom-property.png
labels: [write properties]
---
![已添加到文件的自定义属性](added-custom-property.png){ width=450 }

此 VBA 示例演示了如何使用文档管理器 API 将 *ApprovedBy* 属性添加到所有来源，并将其值设置为当前用户的名称。该属性将被添加（或更新）到文件（通用）、所有配置和所有切割清单项中。

在 *FILE_PATH* 常量中指定文件的完整路径。

{% code-snippet { file-name: Macro.vba } %}