---
layout: sw-tool
title: SOLIDWORKS macro to rename configurations based on custom property
caption: Rename Configurations Based On Custom Property
description: Macro renames all configurations of assembly or part into the value of the specified configuration specific custom property
image: sw-configuration-name.png
labels: [configuration, custom property, rename, solidworks api, utility]
group: Custom Properties
redirect-from:
  - /2018/04/solidworks-api-model-rename-configurations-based-on-custom-prp.html
---
This macro renames all configurations of assembly or part into the value of the specified configuration specific custom property using SOLIDWORKS API.

![Configuration name in the configuration properties manager page](sw-configuration-name.png){ width=200 }

* Run the macro and enter the name of the custom property to read the value from
* Macro will traverse all configurations and rename them based on the corresponding value of the configuration specific custom property
* If property doesn't exist in configuration or value is empty - configuration is not renamed  

{% code-snippet { file-name: Macro.vba } %}
