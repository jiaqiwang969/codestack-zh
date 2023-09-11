---
title: SOLIDWORKS API 中的方法和属性命名
caption: 命名约定
description: 解释 SOLIDWORKS API 对象模型中方法、属性和接口的命名约定（例如 OpenDoc6 vs OpenDoc5）
image: obsolete-api-interface.png
labels: [过时,版本,编号]
---
SOLIDWORKS API（以及 SOLIDWORKS 本身）都是向后兼容的，这意味着旧版本的 API 与新版本的 SOLIDWORKS 兼容。这意味着当新版本发布时，API 方法的签名和行为不应该被改变。为此，SOLIDWORKS 引入了方法和接口名称的修订系统。每当有新版本的 API 可用时，它将以 **MethodName** *Last Revision + 1* 的形式添加到类图中。例如，[ISldWorks::OpenDoc6](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isldworks~opendoc6.html) 是 [ISldWorks::OpenDoc5](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isldworks~opendoc5.html) 方法的更新版本。而 [IModelDoc2](https://help.solidworks.com/2018/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IModelDoc2.html) 是 [IModelDoc](https://help.solidworks.com/2018/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IModelDoc.html) 接口的更新（当前）版本。

## 过时的方法和接口

尽管 SOLIDWORKS 是向后兼容的，所有版本的方法都应该可以工作，但建议使用与 SOLIDWORKS 目标程序的最低版本兼容的最新版本。

主要原因如下：

* 过时的方法（或任何备注和描述）可能在 API 文档中不可用。因此，可能需要维护先前版本的 API 帮助文档。

![过时的 IModelDoc API 接口](obsolete-api-interface.png){ width=250 }

* 并不总是知道添加替代方法的原因。这可能是由于旧版本方法中存在的某个错误（或行为），如果使用该方法，可能会为程序引入未知的副作用。

* 如果出现问题，可能会在寻求支持时遇到问题，因为第一个明显的建议是将方法升级到新版本，而旧方法可能被视为“无保修”。