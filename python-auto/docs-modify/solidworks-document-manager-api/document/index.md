---
标题：使用ISwDMDocument对象在文档管理器API中的示例
说明：与ISwDMDocument接口在文档管理器API中的使用相关的示例
标签：[文档管理器，文档]
顺序：2

[ISwDMDocument](https://help.solidworks.com/2016/english/api/swdocmgrapi/SolidWorks.Interop.swdocumentmgr~SolidWorks.Interop.swdocumentmgr.ISwDMDocument.html) SOLIDWORKS文档管理器API接口表示SOLIDWORKS文件（零件、装配和绘图）的流。文档可以以只读访问或写访问的方式打开。这个选项由[ISwDMApplication::GetDocument](https://help.solidworks.com/2012/english/api/swdocmgrapi/solidworks.interop.swdocumentmgr~solidworks.interop.swdocumentmgr.iswdmapplication~getdocument.html)方法的**allowReadOnly**参数控制。

当以只读方式打开文档时，任何修改都不会被保存。