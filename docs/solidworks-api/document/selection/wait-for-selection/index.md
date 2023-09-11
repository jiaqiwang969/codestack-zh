---
title: Wait for user selection in document using SOLIDWORKS API
caption: Wait For User Selection
description: 2 approaches to wait for the object selected by the user in VBA macro using SOLIDWORKS API
image: selected-edge.png
labels: [selection,event,notification]
---
This article describes two approaches of waiting for the object selection in SOLIDWORKS document using SOLIDWORKS API in VBA macro.

For both approaches specify the filter to wait selection for at the beginning of the macro. Available filter values defined in the [swSelectType_e](https://help.solidworks.com/2014/english/api/swconst/SolidWorks.Interop.swconst~SolidWorks.Interop.swconst.swSelectType_e.html) enumeration

~~~ vb
Const FILTER As Integer = swSelectType_e.swSelEDGES
~~~

## Block the thread waiting for selection

This approach loops the selected objects and blocks the current thread until the required selection is done. *DoEvents* function is called in each iteration to continue message queue so SOLIDWORKS window is not locked

* Run the macro
* Select edge (or the object specified in the filter)

![Selected edge](selected-edge.png){ width=250 }

* Macro stops execution and the reference of *swObject* is set to the selected element

![VBA macro stops once specified object is selected](selection-stop-execution.png){ width=550 }

{% code-snippet { file-name: MacroBlocking.vba } %}

## Handling the selection event

This approach uses the SOLIDWORKS notifications to handle the selection. This is more preferable option as it doesn't block the main thread, however this option requires adding of class module and additional synchronization (depending on the requirements) as events are handled asynchronously.

* Create macro module and class module as shown below

![Macro solution tree](macro-solution-tree.png)

* Run macro and select edge (or the object specified in the filter)
* Similar to the previous approach code stops after the selection and the reference of *swObject* is set to the selected element

![VBA macro stops once specified object is selected via notification](selection-event-stop-execution.png){ width=550 }

### Macro Module

{% code-snippet { file-name: MacroEvent.vba } %}

### EventsListener Class Module

{% code-snippet { file-name: EventsListener.vba } %}
