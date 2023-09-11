---
layout: sw-tool
title: Macro to save all opened documents silently using SOLIDWORKS API
caption: Save All Documents Silently
description: VBA macro to save all currently opened modified documents silently (without the popup messages) using SOLIDWORKS API
image: save-all-documents.png
labels: [save all,silent]
group: Frame
---
This VBA macro allows to save all documents currently opened and modified in SOLIDWORKS silently using SOLIDWORKS API. Unlike default save as command where the various warning messages can be displayed while saving the files this macro will save documents without showing any popup messages.

![Old version warning while saving file](older-version-save-warning.png){ width=350 }

Macro can be configured to either display the error (in case some of the files were not saved properly) or to keep it silent.

~~~ vb
Const SHOW_ERROR As Boolean = False 'True to show message box in case of an error, False to keep it silent
~~~

The result of the operation is displayed in the status bar.

![Result displayed in the status bar](status-bar.png)

This macro can be used as a part of background integration where modal dialogs should not be displayed.

{% code-snippet { file-name: Macro.vba } %}