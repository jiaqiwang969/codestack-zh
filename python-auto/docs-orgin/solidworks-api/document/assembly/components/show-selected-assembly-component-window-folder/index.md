---
layout: sw-tool
title: SOLIDWORKS Macro shows selected assembly component in the Window folder
caption: Show Selected Assembly Component In The Window Folder
description: Example demonstrates how to open the folder of the selected component in the assembly in the Windows File Explorer
image: windows-folder-selected-component.svg
labels: [assembly, component, explorer, frame, macro, show in folder, solidworks, solidworks api, utility, vba]
group: Assembly
redirect-from:
  - /2018/03/show-selected-assembly-component-in.html
  - /solidworks-api/document/assembly/show-selected-assembly-component-window-folder
---
This macro demonstrates how to open the folder of the selected component in the assembly in the Windows File Explorer using SOLIDWORKS API.

The component's file will be preselected in the opened window.

This macro will produce similar results to the following manual steps:

1. Open component in its own window
1. Go to File Menu
1. Select the file from the Open Recent
1. Select "Show In Folder" option

![Open Recent file menu command](open-recent.png){ width=320 height=69 }

If none of the components selected then the path of active model will be opened.

Watch [video demonstration](https://youtu.be/9uZCecGg25I?t=266)

{% code-snippet { file-name: macro.vba } %}
