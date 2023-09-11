---
layout: sw-macro-fix
title: Fix too long SOLIDWORKS VBA macro line error
caption: Too Long VBA Macro Line
description: Fixing the Compile error - Invalid outside procedure error when placing the long text into the VBA macro variable
image: doc-mgr-key-too-long.gif
labels: [macro, troubleshooting]
redirect-from:
  - /2018/04/macro-troubleshooting-too-long-vba-macro-line.html
---
## 症状

* SOLIDWORKS VBA宏正在使用文档管理器API，并生成了新的许可证。
将生成的许可证放入宏中时，一些文本会被标记为红色，并显示“编译错误：无效的外部过程错误”
* 宏正在将静态文本插入到注释或自定义属性中。文本被新的长文本替换。插入的字符串被标记，并且宏无法运行

![将文档管理器许可证密钥复制粘贴到宏常量中](doc-mgr-key-too-long.gif)

## 原因

VBA代码中单行的最大符号数为1023。
如果不显式拆分行，就无法插入更多的符号。
从缓冲区中粘贴超过限制长度的行会导致编译错误。

## 解决方法

将行拆分为多行（单行不超过1023个符号），并使用 "string1" & _ "string2" 来连接这些行。

~~~ vb
Const SW_DM_KEY As String = "MyCompany:swdocmgr_general-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000," & _
"swdocmgr_previews-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000," & _
"swdocmgr_dimxpert-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000," & _
"swdocmgr_geometry-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000," & _
"swdocmgr_xml-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000," & _
"swdocmgr_tessellation-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000-00000"

Dim swDmClassFactory As SwDocumentMgr.swDmClassFactory
Dim swDmApp As SwDocumentMgr.SwDMApplication

Sub main()

    Set swDmClassFactory = CreateObject("SwDocumentMgr.SwDMClassFactory")
    
    If Not swDmClassFactory Is Nothing Then
        Set swDmApp = swDmClassFactory.GetApplication(SW_DM_KEY)
        Debug.Print swDmApp.GetLatestSupportedFileVersion()
    Else
        MsgBox "Document Manager SDK is not installed"
    End If
    
End Sub
~~~

