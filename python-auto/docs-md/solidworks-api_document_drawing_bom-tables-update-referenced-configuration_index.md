---
title: SOLIDWORKS macro to update referenced configuration from BOM tables
caption: Update Referenced Configuration From BOM Tables
description: Macro will update the referenced configurations for all Bill of Materials (BOM) tables on the active drawing document using SOLIDWORKS API
image: bom-configurations-property.png
labels: [bom, default view, referenced configuration, solidworks api, utility, view]
redirect-from:
  - /2018/03/update-referenced-configuration-from.html
---
This macro will update the referenced configurations for all Bill of Materials (BOM) tables on the active drawing document using SOLIDWORKS API.

![List of configurations to use in the BOM table](bom-configurations-property.png){ width=168 height=320 }

Bill of Materials tables are not associated with the drawing views and will exist even in case view is deleted.
BOMs are not linked to the referenced configuration of the view. So if the view's referenced configuration is changed - the BOM won't update.

This macro will find all BOM tables and update their referenced configurations based on the default view of the sheet.

![Use custom properties value from model option in the sheet properties](use-custom-prps-from-view-sheet-property.png){ width=400 height=165 }

{% code-snippet { file-name: Macro.vba } %}
