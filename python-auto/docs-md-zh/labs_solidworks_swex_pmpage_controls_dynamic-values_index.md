---
title: 处理控件中更新的动态值
caption: 动态值
description: 使用SwEx.PMPage框架处理属性管理器页面中更新的控件的动态值
image: controls-dynamic-values.gif
toc-group-name: labs-solidworks-swex
order: 13
---
![更新的控件值](controls-dynamic-values.gif)

为了在代码后台动态更新属性更改的控件值（例如在按钮点击时或当一个属性更改时），需要在数据模型中实现[INotifyPropertyChanged](https://docs.microsoft.com/zh-cn/dotnet/api/system.componentmodel.inotifypropertychanged?view=netframework-4.8)。对于每个需要监视的属性，引发[PropertyChanged](https://docs.microsoft.com/zh-cn/dotnet/api/system.componentmodel.inotifypropertychanged.propertychanged?view=netframework-4.8)事件，通知环境值已更改并且控件需要更新。

{% code-snippet { file-name: DynamicValues.* } %}