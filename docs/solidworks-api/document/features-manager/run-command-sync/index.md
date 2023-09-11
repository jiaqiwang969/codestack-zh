---
title: How to run commands synchronously using SOLIDWORKS API
caption: Run Command Synchronously
description: Example demonstrates how to run SOLIDWORKS commands synchronously (i.e. return the execution once command closed)
image: command_open.png
labels: [sync, command, close]
---
![Opened Command (Property Manager Page)](command_open.png){ width=250 }

[ISldWorks::RunCommand](https://help.solidworks.com/2017/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isldworks~runcommand.html) SOLIDWORKS API method allows running any command. Usually it is used to open property manager page.

However this command runs asynchronously, which means that the control is returned to the executor once command started (e.g. Property Manager Page is opened). In some cases it is required to execute the code once this command closes (e.g. Property Manager Page is closed).

This example demonstrates how to run command synchronously using SOLIDWORKS API, so the control is returned to the executor once the command finishes (not started).

## Run Instructions

* Open/create part document
* Create any sketch with rectangle (or another shape)
* Select the sketch
* Run the macro. As the result 'Boss-Extrude' property page is displayed
* Modify options and click green tick (OK) or cross (Cancel)
* Macro displays the message when property page is closed and the result (OK or Cancel) is displayed

### VBA Macro

* Create a class module and name it *CommandRunManager*. Copy the code below:

{% code-snippet { file-name: CommandRunManager.vba } %}

* Copy the following code into the main module (where the *main* function is)
* Modify the *RunCommand* to pass any other command id if needed. Method returns True if the command is closed with OK button, False is returned when command is cancelled.

{% code-snippet { file-name: Macro.vba } %}

### C&#35;

It is not recommended to use DoEvents function to emulate async operation in .NET languages (C# or VB.NET). It is better to use [Asynchronous programming with async and await](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/async/)

Example below demonstrates an implementation of async version of RunCommand which can be awaited without locking of the UI thread:

**SldWorksExtension.cs**

{% code-snippet { file-name: SldWorksExtension.cs } %}

The extension can be called from any async method. For example

{% code-snippet { file-name: Console.cs } %}
