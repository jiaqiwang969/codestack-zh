---
title: Write custom property to file, configuration and cut-list using SOLIDWORKS API
caption: Write All Properties
description: VBA macro example to write different types of properties (general, configuration specific and cut list) using SOLIDWORKS API
image: approved-date-custom-property.png
labels: [set property,add property,write property,date]
---
![Date custom property](approved-date-custom-property.png){ width=550 }

This VBA macro example demonstrates how to add (create new or change existing) custom properties to various custom properties sources using SOLIDWORKS API. This includes file (general) custom properties, configuration specific custom properties and cut-list items (weldment or sheet metal) custom properties.

Macro adds the *ApprovedDate* custom property of type *Date* and sets the value to the current date.

> By some reasons custom property field type is ignored and defaulted to Text when assigned to cut-list item

{% code-snippet { file-name: Macro.vba } %}
