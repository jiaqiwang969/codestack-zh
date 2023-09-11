---
title: Write summary information to the active file using SOLIDWORKS API
caption: Write Summary Information
description: VBA macro to fill the summary information (author, keywords, comments, title, subject) for active SOLIDWORKS file using SOLIDWORKS API
image: summary.png
labels: [summary info,write summary]
---
![SOLIDWORKS文件的摘要信息](summary.png){ width=500 }

这个VBA宏使用SOLIDWORKS API，填写活动模型的自定义属性的*摘要信息*标签（作者、关键词、注释、标题和主题）。

配置宏并指定要写入的值：

~~~ vb
Const AUTHOR As String = "CodeStack"
Const KEYWORDS As String = "sample,summary,api"
Const COMMENTS As String = "Example comments"
Const TITLE As String = "Summary API Example"
Const SUBJECT As String = "CodeStack API Examples"
~~~

~~~ vb
Const AUTHOR As String = "CodeStack"
Const KEYWORDS As String = "sample,summary,api"
Const COMMENTS As String = "Example comments"
Const TITLE As String = "Summary API Example"
Const SUBJECT As String = "CodeStack API Examples"

Dim swApp As SldWorks.SldWorks

Sub main()

    Set swApp = Application.SldWorks
    
    Dim swModel As SldWorks.ModelDoc2
    
    Set swModel = swApp.ActiveDoc
    
    If Not swModel Is Nothing Then
        swModel.SummaryInfo(swSummInfoField_e.swSumInfoAuthor) = AUTHOR
        swModel.SummaryInfo(swSummInfoField_e.swSumInfoKeywords) = KEYWORDS
        swModel.SummaryInfo(swSummInfoField_e.swSumInfoComment) = COMMENTS
        swModel.SummaryInfo(swSummInfoField_e.swSumInfoTitle) = TITLE
        swModel.SummaryInfo(swSummInfoField_e.swSumInfoSubject) = SUBJECT
    Else
        MsgBox "Please open model"
    End If
    
End Sub
~~~

