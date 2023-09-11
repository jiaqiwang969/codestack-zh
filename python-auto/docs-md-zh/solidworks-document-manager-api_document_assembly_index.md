---
标题：使用SOLIDWORKS文档管理器API处理装配文档
说明：包含使用文档管理器API处理装配文档的示例集合
---
与常规的SOLIDWORKS API不同，文档管理器没有为装配文档提供特定的接口，而是应由[ISwDMDocument](https://help.solidworks.com/2016/english/api/swdocmgrapi/SolidWorks.Interop.swdocumentmgr~SolidWorks.Interop.swdocumentmgr.ISwDMDocument.html)和[ISwDMConfiguration2](https://help.solidworks.com/2018/english/api/swdocmgrapi/SolidWorks.Interop.swdocumentmgr~SolidWorks.Interop.swdocumentmgr.ISwDMConfiguration2.html)接口进行管理。

这些接口中的一些方法仅适用于装配文档，例如[ISwDMConfiguration2::GetComponents](https://help.solidworks.com/2018/english/api/swdocmgrapi/solidworks.interop.swdocumentmgr~solidworks.interop.swdocumentmgr.iswdmconfiguration2~getcomponents.html)或[ISwDMDocument8::GetComponentCount](https://help.solidworks.com/2018/english/api/swdocmgrapi/solidworks.interop.swdocumentmgr~solidworks.interop.swdocumentmgr.iswdmdocument8~getcomponentcount.html)。

建议使用[SOLIDWORKS文档管理器API的ISwDMDocument::FullName](https://help.solidworks.com/2018/english/api/swdocmgrapi/SolidWorks.Interop.swdocumentmgr~SolidWorks.Interop.swdocumentmgr.ISwDMDocument~FullName.html)来获取完整路径，并将其扩展名与.sldasm进行匹配，以验证文档是否为装配。

本节包含与使用文档管理器处理装配文档相关的示例和宏。