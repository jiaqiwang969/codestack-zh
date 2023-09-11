标题：使用SOLIDWORKS文档管理器API管理文件的自定义属性
标题：自定义属性
描述：使用SOLIDWORKS文档管理器API为文件添加、删除、修改、读取自定义属性（可见和不可见）
标签：[自定义属性]

SOLIDWORKS文档管理器API提供了一套全面的函数来管理（添加、删除、修改和读取）SOLIDWORKS文件中的自定义属性。

可以通过以下方式访问自定义属性：

* 通过[ISwDMDocument](https://help.solidworks.com/2018/english/api/swdocmgrapi/SolidWorks.Interop.swdocumentmgr~SolidWorks.Interop.swdocumentmgr.ISwDMDocument.html)接口访问文件（通用）的自定义属性
* 通过[ISwDMConfiguration](https://help.solidworks.com/2018/english/api/swdocmgrapi/SolidWorks.Interop.swdocumentmgr~SolidWorks.Interop.swdocumentmgr.ISwDMConfiguration.html)接口访问配置的自定义属性
* 通过[ISwDMCutListItem2](https://help.solidworks.com/2018/english/api/swdocmgrapi/SolidWorks.Interop.swdocumentmgr~SolidWorks.Interop.swdocumentmgr.ISwDMCutListItem2.html)接口访问切割清单项的自定义属性

可以逐个读取属性，也可以批量提取值。

该库允许提取解析后的值和文本表达式。然而，无法解析值，只能提取缓存的值。例如，如果配置特定的属性包含一个计算模型质量的表达式，并且从未激活过该配置，则文档管理器无法提取计算后的值，直到打开并保存模型，并激活和重建配置。

文档管理器还可以管理不可见属性，这些属性在“自定义属性”对话框中不存在，只能通过文档管理器API读取和写入。

请浏览本节中的文章，了解更多信息和代码示例。