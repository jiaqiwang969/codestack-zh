---
title: Script generates model from input parameters using SOLIDWORKS API
caption: Model Generator
description: Script generating model based on the template with specified parameters using SOLIDWORKS API
image: model-parameters.png
labels: [dimension, parameters, script]
---
This PowerShell script allows generating model using SOLIDWORKS API based on the template with specified parameters

* Create two files and paste the code from the below snippets

## model-generator.ps1
{% code-snippet { file-name: model-generator.ps1 } %}

## model-generator.cmd
{% code-snippet { file-name: model-generator.cmd } %}

Download [Template Model](template.SLDPRT) and save it to the same folder where the above two scripts are saved.

This is template model which has 3 driving parameters: width, height and length.

![Model with parameters](model-parameters.png){ width=350 }

This will be modified by the script and saved to a new file.

* Start the command line and execute the following command

~~~ bat
[Full Path To model-generator.cmd] [Full Path To Output SOLIDWORKS file] [Width] [Length] [Height]
~~~

As the result the file is generated and the process log is displayed directly in the console:

![Messages in console reporting the progress and the result of model generation](console-output.png){ width=450 }

Template file is not modified and the resulting model is saved with the parameters updated.

![Generated model with applied parameters](model-result.png){ width=350 }