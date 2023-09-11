---
caption: Batch Export Models
title: Batch export SOLIDWORKS models via vbScript
description: Example of batch exporting SOLIDWORKS documents from the vbScript
---
这个示例演示了如何使用 vbScript 批量导出 SOLIDWORKS 文档

## 参数

1. SOLIDWORKS 模型所在文件夹的路径
1. 输入文件扩展名的过滤器
1. 输出文件夹的路径
1. 输出格式的扩展名

~~~
> "export-sw-models.vbs" "C:\Models" sldprt "C:\Output" step
~~~

~~~ vbs
Dim dirPath
dirPath = WScript.Arguments.Item(0)

Dim filter
filter = WScript.Arguments.Item(1)

Dim outDir
outDir = WScript.Arguments.Item(2)

Dim outExt
outExt = WScript.Arguments.Item(3)

Dim swApp
Set swApp = CreateObject("SldWorks.Application")
swApp.Visible = True

Dim fso
Set fso = CreateObject("Scripting.FileSystemObject")

Dim folder
Set folder = fso.GetFolder(dirPath)

dim file

For Each file in folder.Files
    If LCase(fso.GetExtensionName(file.Path)) = LCase(filter) Then
        Dim docSpec
        Set docSpec = swApp.GetOpenDocSpec(file.Path)
        docSpec.ReadOnly = True

        Dim swModel
        Set swModel = swApp.OpenDoc7(docSpec)

        If Not swModel is Nothing Then
            Dim outFilePath
            outFilePath = outDir & "\" & fso.GetBaseName(file) & "." & outExt
            swModel.SaveAs outFilePath
            swApp.CloseDoc swModel.GetTitle()
        End If
    End If
Next

swApp.ExitApp
~~~

