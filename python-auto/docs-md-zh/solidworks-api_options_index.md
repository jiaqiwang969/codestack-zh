---
标题：使用SOLIDWORKS API管理系统选项和用户首选项
说明：使用SOLIDWORKS API控制文档和应用程序级别的用户首选项和系统选项的文章和示例
图片：solidworks-options.svg
标签：[首选项，选项]
顺序：8
---

![SOLIDWORKS选项API自动化](solidworks-options.svg){ width=250 }

大多数SOLIDWORKS选项都是通过SetUserPreference SOLIDWORKS API方法来控制的。有多个版本的方法来控制文本、整数、开关、数值等属性。

找到所需用户首选项的标识符最简单的方法是使用以下[系统选项表](https://help.solidworks.com/2018/english/api/sldworksapiprogguide/overview/system_options_and_document_properties.htm)或者简单地[录制宏](/solidworks-api/getting-started/macros/recording)并更改目标属性。相应的SOLIDWORKS API调用将被写入宏中。

所有系统选项可以分为两个类别：应用程序级别和文档级别。

本节包含了用于自动化用户首选项和应用程序设置的代码示例和宏。