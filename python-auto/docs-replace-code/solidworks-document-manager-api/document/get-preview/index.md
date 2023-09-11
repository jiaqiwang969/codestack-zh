---
标题：使用SOLIDWORKS文档管理器API从活动配置中提取PNG预览图像
说明：示例演示了如何使用文档管理器API从SOLIDWORKS装配或零件的活动配置中提取PNG预览图像。

此方法适用于内部和外部应用程序。

- 创建C#控制台应用程序
- 粘贴代码
- 使用两个参数运行应用程序：输入SOLIDWORKS零件或装配的完整路径和输出PNG图像的完整路径

此示例使用[SOLIDWORKS文档管理器API的ISwDMConfiguration9::GetPreviewPNGBitmapBytes](https://help.solidworks.com/2018/english/api/swdocmgrapi/solidworks.interop.swdocumentmgr~solidworks.interop.swdocumentmgr.iswdmconfiguration9~getpreviewpngbitmapbytes.html)方法提取预览的字节缓冲区，并将其转换为[Image](https://docs.microsoft.com/en-us/dotnet/api/system.drawing.image?view=netframework-4.7.2)对象。

~~~ cs
using SwDocumentMgr;
using System;
using System.Drawing;
using System.IO;

namespace CodeStackExample
{
    class Program
    {
        const string LICENSE_KEY = "[Document Manager License Key]";

        static void Main(string[] args)
        {
            var filePath = args[0];
            var outImgFilePath = args[1];

            var classFact = new SwDMClassFactory();

            var app = classFact.GetApplication(LICENSE_KEY);

            var docType = SwDmDocumentType.swDmDocumentUnknown;

            switch (Path.GetExtension(filePath).ToLower())
            {
                case ".sldprt":
                    docType = SwDmDocumentType.swDmDocumentPart;
                    break;

                case ".sldasm":
                    docType = SwDmDocumentType.swDmDocumentAssembly;
                    break;

                case ".slddrw":
                    docType = SwDmDocumentType.swDmDocumentDrawing;
                    break;
            }

            SwDmDocumentOpenError err;
            var doc = app.GetDocument(filePath, docType, true, out err);

            if (doc != null)
            {
                var activeConfName = doc.ConfigurationManager.GetActiveConfigurationName();

                var conf = doc.ConfigurationManager.GetConfigurationByName(activeConfName) as ISwDMConfiguration14;

                SwDmPreviewError previewErr;
                var imgBytes = conf.GetPreviewPNGBitmapBytes(out previewErr) as byte[];

                if (previewErr == SwDmPreviewError.swDmPreviewErrorNone)
                {
                    using (var memStr = new MemoryStream(imgBytes))
                    {
                        memStr.Seek(0, SeekOrigin.Begin);
                        var img = Image.FromStream(memStr);
                        img.Save(outImgFilePath);
                    }
                }
                else
                {
                    Console.WriteLine($"Failed to extract preview from the document: {previewErr}");
                }
            }
            else
            {
                Console.WriteLine($"Failed to open the document: {err}");
            }
        }
    }
}
~~~

