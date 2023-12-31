---
layout: sw-tool
title: Export SOLIDWORKS files using SOLIDWORKS API in shell script
caption: Export Files
description: Script allows exporting of the SOLIDWORKS file into the foreign format using command line
image: power-shell-export.svg
labels: [export, script]
group: Import/Export
---
这个PowerShell脚本允许使用SOLIDWORKS API从命令行将SOLIDWORKS文件导出为指定的外部格式。

## 配置和使用说明

* 创建两个文件，并从下面的代码片段中粘贴代码

### export-file.ps1
~~~ ps1
$inputFilePath=$args[0]
$outFilePath=$args[1]

$ScriptDir = Split-Path $script:MyInvocation.MyCommand.Path

$Assem = ( 
    $ScriptDir + "\SolidWorks.Interop.sldworks.dll"
    ) 
    
$Source = @"
using SolidWorks.Interop.sldworks;
using System;

 namespace CodeStack
 {
    public static class Exporter
    {
        #region Libraries
        
        static Exporter()
        {
            AppDomain.CurrentDomain.AssemblyResolve += OnAssemblyResolve;
        }

        public static void LoadLibrary(params object[] libs)
        {
            foreach(string lib in libs)
            {
                Console.WriteLine(string.Format("Loading library: {0}", lib));
                System.Reflection.Assembly assm = System.Reflection.Assembly.LoadFrom(lib);
                Console.WriteLine(assm.GetName().ToString());
            }
        }
        
        private static System.Reflection.Assembly OnAssemblyResolve(object sender, ResolveEventArgs args)
        {
            foreach (System.Reflection.Assembly assm in AppDomain.CurrentDomain.GetAssemblies())
            {
               if(assm.GetName().ToString() == args.Name)
               {
                   return assm;
               }
            };
            
            return null;
        }
        
        #endregion
        
        public static void ExportFile(string filePath, string outFilePath)
        {
            Console.WriteLine("Connecting to SOLIDWORKS...");

            ISldWorks app = Activator.CreateInstance(Type.GetTypeFromProgID("SldWorks.Application")) as ISldWorks;

            if (app != null)
            {
                Console.WriteLine(string.Format("Opening file '{0}'...", filePath));

                IDocumentSpecification docSpec = app.GetOpenDocSpec(filePath) as IDocumentSpecification;
                docSpec.ReadOnly = true;
                docSpec.Silent = true;
                IModelDoc2 model = app.OpenDoc7(docSpec);

                if (model != null)
                {
                    const int swSaveAsCurrentVersion = 0;
                    const int swSaveAsOptions_Silent = 1;
                    int err = -1;
                    int warn = -1;

                    Console.WriteLine(string.Format("Exporting file '{0}' to '{1}'...", filePath, outFilePath));

                    if (!model.Extension.SaveAs(outFilePath, swSaveAsCurrentVersion,
                        swSaveAsOptions_Silent, null, ref err, ref warn))
                    {
                        Console.WriteLine(string.Format("Failed to export '{0}' to '{1}'. Error code: {2}", filePath, outFilePath, err));
                    }

                    Console.WriteLine(string.Format("Closing file '{0}'...", filePath));

                    app.CloseDoc(model.GetTitle());
                }
                else
                {
                    Console.WriteLine(string.Format("Failed to open document: '{0}'. Error code: {1}",
                        filePath, docSpec.Error));
                }
            }
            else
            {
                Console.WriteLine("Failed to connect to SOLIDWORKS instance");
            }
        }
    }
}
"@
 
Add-Type -TypeDefinition $Source -ReferencedAssemblies $Assem -Language CSharp
 
[CodeStack.Exporter]::LoadLibrary($Assem)
[CodeStack.Exporter]::ExportFile($inputFilePath, $outFilePath)
~~~



### export-file.cmd
~~~ cmd
SET inputFilePath=%1
SET outFilePath=%2

PowerShell -NoProfile -ExecutionPolicy Bypass -File "%~dp0export-file.ps1" %inputFilePath% %outFilePath%
~~~



* 将*SolidWorks.Interop.sldworks.dll*复制到创建上述脚本的文件夹中。PowerShell脚本基于.NET Framework 2.0，因此SOLIDWORKS interop必须针对此框架。该dll可以在以下位置找到：**SOLIDWORKS安装文件夹**\api\redist\CLR2\SolidWorks.Interop.sldworks.dll

![文件夹中的脚本数据文件](script-folder.png){ width=450 }

或者可以指定SOLIDWORKS interop的完整路径，如下所示。在这种情况下，不需要将此dll复制到脚本文件夹中。

~~~ ps1
$Assem = ( 
   "SolidWorks.Interop.sldworks.dll的完整路径"
    ) 
~~~

* 启动命令行并执行以下命令

~~~ bat
[export-file.cmd的完整路径] [输入SOLIDWORKS文件的完整路径] [输出文件的完整路径和扩展名]
~~~

结果文件将被导出，并且进程日志将直接显示在控制台中：

![在控制台中报告导出进度和结果的消息](export-file-result-console.png){ width=450 }