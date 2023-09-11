---
title: Read summary information from file using SOLIDWORKS API
caption: Read Summary Information
description: VBA macro to extract the summary information (e.g. author, keywords, comments, title, creation info etc.) for active SOLIDWORKS file using SOLIDWORKS API
image: summary.png
labels: [summary info,author,comments,title]
---
![Summary Information of SOLIDWORKS file](summary.png){ width=500 }

This VBA macro extracts the data from the *Summary Information* tab from custom properties of the active SOLIDWORKS document using SOLIDWORKS API. This information includes author, keywords, comments, title, creation info, last saved info.

This macro additionally extracts the SOLIDWORKS version the file was created in.

Result is output to the [immediate window of VBA editor](/visual-basic/vba/vba-editor/windows#immediate-window) in the following format:

~~~
Author: CodeStack
Keywords: sample,summary,api
Comments: Example comments
Title: Summary API Example
Subject: CodeStack API Examples
Created: Tuesday, 10 September 2019 10:35:37 AM
Last Saved: Tuesday, 10 September 2019 11:08:23 AM
Last Saved By: artem.taturevych
Last Saved With: SOLIDWORKS 2019
Created With: SOLIDWORKS 2012
~~~

{% code-snippet { file-name: Macro.vba } %}
