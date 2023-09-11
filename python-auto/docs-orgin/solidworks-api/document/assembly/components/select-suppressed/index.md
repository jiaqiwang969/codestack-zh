---
title: Select all suppressed components in the assembly using SOLIDWORKS API
caption: Select All Suppressed Components
description: VBA macro which runs the 'Component Selection - Select Suppressed' command in assembly document to select all assembly components in a batch
image: select-suppressed-components.png
labels: [command,suppressed,components]
---
This VBA macro allows to select all suppressed components in the active SOLIDWORKS assembly in a batch using SOLIDWORKS and Windows API.

This executes the *Select Suppressed* command of *Component Selection* menu

![Select Suppressed command for components](select-suppressed-components.png){ width=500 }

This is preferable option of selecting all suppressed components over the [traversing components](/solidworks-api/document/assembly/components/traversing-tree) one-by-one due to the performance benefits.

{% code-snippet { file-name: Macro.vba } %}