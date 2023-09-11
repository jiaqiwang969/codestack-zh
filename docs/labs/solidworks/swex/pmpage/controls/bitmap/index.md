---
title: Bitmap control in SOLIDWORKS property Manager Page
caption: Bitmap
description: Creating bitmap control in the Property Manager Page using SwEx.PMPage framework
image: bitmap.png
toc-group-name: labs-solidworks-swex
order: 11
---
![Bitmap control](bitmap.png)

Static bitmap will be created in the property manager page for the properties of [Image](https://docs.microsoft.com/en-us/dotnet/api/system.drawing.image?view=netframework-4.8) type or other types assignable from this type, e.g. [Bitmap](https://docs.microsoft.com/en-us/dotnet/api/system.drawing.bitmap?view=netframework-4.8)

{% code-snippet { file-name: Bitmap.* } %}

## Bitmap size

Default size of the bitmap is 18x18 pixels, however this could be overridden using the [BitmapOptionsAttribute](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_Attributes_BitmapOptionsAttribute.htm) by providing width and height values in the constructor parameters:

{% code-snippet { file-name: Bitmap.Size.* } %}

> Due to SOLIDWORKS API limitation bitmap cannot be changed as [dynamic value](/labs/solidworks/swex/pmpage/controls/dynamic-values/) after property manager page is displayed. Assign the image in the data model class constructor or as a default value of the property.
