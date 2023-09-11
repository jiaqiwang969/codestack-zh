---
layout: sw-tool
title: 将SOLIDWORKS文件特定的自定义属性复制到配置
caption: 将文件特定的自定义属性复制到配置属性
description: 该宏将所有文件特定属性复制到活动配置的属性中
image: file-specific-custom-properties.png
labels: [配置, 复制, 自定义属性, 实用工具]
group: 自定义属性
redirect-from:
  - /2018/03/copy-file-specific-custom-properties-to.html
---
该宏使用SOLIDWORKS API将所有文件特定属性复制到活动配置的属性中。

![文件的自定义选项卡中的属性](file-specific-custom-properties.png){ width=640 }

{% code-snippet { file-name: Macro.vba } %}