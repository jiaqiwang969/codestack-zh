---
title: Select Named Entity (face, edge or vertex) using SOLIDWORKS API
caption: Select Named Entity
description: Select named entity (face, edge or vertex) in part, assembly (from component) or drawing (from view) using SOLIDWORKS API
image: face-name.png
labels: [face,edge,vertex,name,selection]
---
This example demonstrates how to select a named entity (face, edge or vertex) in the different document types using SOLIDWORKS API.

Named entity can be only defined in the part document by selecting corresponding face or edge:

![Face properties command in context menu](face-properties.png){ width=250 }

Name can be set in the displayed dialog and it is unique per part.

![Face name dialog](face-name.png){ width=250 }

Pointer to the entity can be retrieved via [IPartDoc::GetEntityByName](https://help.solidworks.com/2014/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IPartDoc~GetEntityByName.html) SOLIDWORKS API method.

This example enhances the functionality and also allows to select entity by name in drawing (from the selected drawing view) or assembly (from the selected component of part).

Modify the value of the *ENT_NAME* constant to define different name and change the value of *entType* argument if edge or vertex needs to be selected

~~~ vb
Const ENT_NAME As String = "MyEdge1"
SelectNamedEntity swParentObject, ENT_NAME, NamedEntityType_e.Edge
~~~

{% code-snippet { file-name: Macro.vba } %}
