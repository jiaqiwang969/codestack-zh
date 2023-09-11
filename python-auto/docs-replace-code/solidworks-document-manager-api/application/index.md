---
标题：在SOLIDWORKS文档管理器API中利用主要ISwDMApplication应用对象
说明：ISwDMApplication是Document Manager API中的顶级对象，表示应用程序本身。
链接：[ISwDMApplication](https://help.solidworks.com/2017/english/api/swdocmgrapi/solidworks.interop.swdocumentmgr~solidworks.interop.swdocumentmgr.iswdmapplication.html)

通过ISwDMClassFactory::GetApplication方法可以访问该对象的指针。

### 功能

* 访问文档（即打开文档流）
* 对文档进行操作（移动、复制），并能够保留引用
* 创建数据对象（如搜索选项或外部引用选项）