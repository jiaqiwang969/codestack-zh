---
title: Managing system options (application level) using SOLIDWORKS API
caption: Application Options
description: Collection of articles and examples which demonstrate how to control application (system) options (user preferences) using SOLIDWORKS API
labels: [document, preferences, options]
---
系统或应用程序级别的选项是在SOLIDWORKS选项对话框中可用的设置。可以使用以下SOLIDWORKS API来控制这些值：

提取当前选项的值：

* [ISldWorks::GetUserPreferenceDoubleValue](https://help.solidworks.com/2018/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.ISldWorks~GetUserPreferenceDoubleValue.html)

* [ISldWorks::GetUserPreferenceIntegerValue](https://help.solidworks.com/2018/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.ISldWorks~GetUserPreferenceIntegerValue.html) 

* [ISldWorks::GetUserPreferenceStringValue](https://help.solidworks.com/2018/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.ISldWorks~GetUserPreferenceStringValue.html)

* [ISldWorks::GetUserPreferenceToggle](https://help.solidworks.com/2018/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.ISldWorks~GetUserPreferenceToggle.html)

更改选项值：

* [ISldWorks::SetUserPreferenceDoubleValue](https://help.solidworks.com/2018/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.ISldWorks~SetUserPreferenceDoubleValue.html)

* [ISldWorks::SetUserPreferenceIntegerValue](https://help.solidworks.com/2018/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.ISldWorks~SetUserPreferenceIntegerValue.html) 

* [ISldWorks::SetUserPreferenceStringValue](https://help.solidworks.com/2018/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.ISldWorks~SetUserPreferenceStringValue.html)

* [ISldWorks::SetUserPreferenceToggle](https://help.solidworks.com/2018/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.ISldWorks~SetUserPreferenceToggle.html)

本节包含使用SOLIDWORKS API管理（读取、写入、复制）各种应用程序级别系统选项的宏和代码示例。