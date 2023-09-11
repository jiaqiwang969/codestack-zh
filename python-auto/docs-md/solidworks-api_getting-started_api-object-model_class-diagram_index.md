---
title: SOLIDWORKS API Object Model class hierarchy diagram
caption: Class Diagram Relationship
description: Detailed explanation of relationships (class diagram) between classes and interfaces in the SOLIDWORKS API Objects Model
image: class-diagram.png
labels: [hierarchy, classes, model]
order: 1
scripts:
    - "scripts/svg-pan-zoom.min.js"
---
Diagram below displays the relationship between interfaces in the SOLIDWORKS API Object model. This is not a complete class hierarchy rather the representation of the mostly commonly used methods and interfaces.

Diagram is interactive, it is possible to zoom in and zoom out with mouse wheel as well as pan with right or left mouse button. Navigation control in the bottom right corner allows to zoom in and zoom out as well as zoom to fit

![Control Box](control-box.png)

All boxes and arrows are clickable and will redirect for the information page about particular method, property or interface.

![Open Link](open-link.png){ width=250 }

<div id="container" style="width: 100%; height: 800px; border:1px solid black; ">
    {% embed file-name: solidworks-api-class-diagram.svg %}
</div>

<script>
var panZoom = svgPanZoom(document.getElementById('solidworks-api-class-diagram'), {
        zoomEnabled: true,
        controlIconsEnabled: true,
        fit: true,
        center: true,
    });
window.addEventListener("resize", function(){
        panZoom.resize();
    });
</script>

## Legend

<img src="legend/init-box.svg" alt="Initialize"> Represents the entry point of the program. This could be a constructor of the class, connection method, macro entry point

<img src="legend/interface-box.svg" alt="Interface Box"> Represents the interface (object) of the SOLIDWORKS API

<img src="legend/cast.svg" alt="Casting"> Represents the relation between interfaces via direct casting (Query Interface)

<img src="legend/method-property.svg" alt="Method or Property"> Represents the relation between interface via method or property

<img src="legend/group.svg" alt="Group"> Represents a group of interfaces

<img src="legend/selection-interface-box.svg" alt="Selection Interface Box"> Represents an interface which is a selectable object in SOLIDWORKS User Interface

<img src="legend/selection-box.svg" alt="Selection Box"> Represents the placeholder for all selectable objects (i.e. the interfaces with blue background)

<img src="legend/etc-box.svg" alt="Etc. Box"> Represents the placeholder for other interface which are part of this group

<img src="legend/etc-box-wildcard.svg" alt="Etc. Box with wildcard"> Represents the placeholder for other interfaces which are part of this group. Interfaces name will match the wildcard
