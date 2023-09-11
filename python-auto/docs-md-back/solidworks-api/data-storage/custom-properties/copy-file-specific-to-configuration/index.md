---
layout: sw-tool
title: Copy SOLIDWORKS file specific custom properties to configuration
caption: Copy File Specific Custom Properties To Configuration Properties
description: Macro copies all the file specific properties into the properties of the active configuration
image: file-specific-custom-properties.png
labels: [configuration, copy, custom properties, utility]
group: Custom Properties
redirect-from:
  - /2018/03/copy-file-specific-custom-properties-to.html
---
该宏使用SOLIDWORKS API将所有文件特定属性复制到活动配置的属性中。

![文件的自定义选项卡中的属性](file-specific-custom-properties.png){ width=640 }

{% code-snippet { file-name: Macro.vba } %}