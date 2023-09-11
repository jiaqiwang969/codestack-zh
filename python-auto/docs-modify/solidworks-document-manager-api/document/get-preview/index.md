---
标题：使用SOLIDWORKS文档管理器API从活动配置中提取PNG预览图像
说明：示例演示了如何使用文档管理器API从SOLIDWORKS装配或零件的活动配置中提取PNG预览图像。

此方法适用于内部和外部应用程序。

- 创建C#控制台应用程序
- 粘贴代码
- 使用两个参数运行应用程序：输入SOLIDWORKS零件或装配的完整路径和输出PNG图像的完整路径

此示例使用[SOLIDWORKS文档管理器API的ISwDMConfiguration9::GetPreviewPNGBitmapBytes](https://help.solidworks.com/2018/english/api/swdocmgrapi/solidworks.interop.swdocumentmgr~solidworks.interop.swdocumentmgr.iswdmconfiguration9~getpreviewpngbitmapbytes.html)方法提取预览的字节缓冲区，并将其转换为[Image](https://docs.microsoft.com/en-us/dotnet/api/system.drawing.image?view=netframework-4.7.2)对象。

{% code-snippet { file-name: console.cs } %}