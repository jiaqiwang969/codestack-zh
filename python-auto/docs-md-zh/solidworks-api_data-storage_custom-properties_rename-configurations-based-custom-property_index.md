---
布局：sw-tool
标题：基于自定义属性重命名配置的SOLIDWORKS宏
说明：该宏使用SOLIDWORKS API将装配体或零件的所有配置重命名为指定配置特定自定义属性的值。
图片：sw-configuration-name.png
标签：[配置，自定义属性，重命名，solidworks api，实用工具]
分组：自定义属性
重定向自：
  - /2018/04/solidworks-api-model-rename-configurations-based-on-custom-prp.html
---

该宏使用SOLIDWORKS API将装配体或零件的所有配置重命名为指定配置特定自定义属性的值。

![配置属性管理器页面中的配置名称](sw-configuration-name.png){ width=200 }

- 运行宏并输入要从中读取值的自定义属性的名称
- 宏将遍历所有配置并根据相应的配置特定自定义属性的值进行重命名
- 如果属性在配置中不存在或值为空，则不会重命名配置

{% code-snippet { file-name: Macro.vba } %}