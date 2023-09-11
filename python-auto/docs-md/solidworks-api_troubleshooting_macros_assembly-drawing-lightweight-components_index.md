---
layout: sw-macro-fix
title: Fix SOLIDWORKS macro issues with lightweight components in assembly or drawing
caption: Lightweight Components In Assembly Or Drawing
description: Fixing the Run-time Error '91' - Object variable or With block variable not set when macro is working with the components in the assembly
image: lightweight-component.png
labels: [macro, troubleshooting]
redirect-from:
  - /2018/04/macro-troubleshooting-lightweight-components-in-assembly.html
---
## Symptoms

SOLIDWORKS macro is working with the components in the assembly (e.g. reading/writing properties, materials, working with features etc.).
Error *Run-time Error '91': Object variable or With block variable not set* is displayed when macro is run.

## Cause

Components can be loaded lightweight which means that their underlying model is not loaded into the memory.
In this case all APIs of the component's model are not available

![Lightweight component in the Feature Manager Tree](lightweight-component.png)

## Resolutions

* Check if the pointer to reference model is not null. Display the error message to the user
* Use [AssemblyDoc::ResolveAllLightWeightComponents](https://help.solidworks.com/2016/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.iassemblydoc~resolvealllightweightcomponents.html) or [AssemblyDoc::ResolveAllLightWeight](https://help.solidworks.com/2016/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IAssemblyDoc~ResolveAllLightweight.html) method to forcibly resolve components states

{% code-snippet { file-name: get-selected-component-material.vba } %}
