---
title: Get the sheet body geometry type using SOLIDWORKS API
caption: Get The Sheet Body Geometry Type
description: Example identifies the type of the selected sheet body (open shell, internal shell, external shell)
image: face-shell-types.png
labels: [example, face, geometry, open geometry, shell, solidworks api, topology]
redirect-from:
  - /2018/03/solidworks-api-geometry-get-body-geometry-type.html
---
在SOLIDWORKS体中有3种类型的面：

* **开放壳体**。与相连面一起，不形成封闭几何体的图纸体面（例如平面面，而壳体立方体或球体的面不会被视为开放）
* **内部壳体**。属于实体体中的空腔的面。
* **外部壳体**。不属于前两组的其他面。

![面的壳体类型](face-shell-types.png){ width=400 height=243 }

下面的示例使用SOLIDWORKS API来识别所选图纸体的类型。如果图纸体是开放几何（包含开放壳体面）或封闭几何（没有开放壳体面），则可以将封闭几何图纸体转换为实体体。

~~~ cs
using System;
using SolidWorks.Interop.sldworks;
using SolidWorks.Interop.swconst;

namespace CodeStack
{
    public partial class SolidWorksMacro
    {
        public enum FaceShellType_e
        {
            Open = 0,
            Internal = 1,
            External = 2
        }

        public void Main()
        {
            IModelDoc2 model = swApp.IActiveDoc2;

            if (model != null)
            {
                SelectionMgr selMgr = model.ISelectionManager;

                IBody2 body = selMgr.GetSelectedObject6(1, -1) as IBody2;

                if (body != null)
                {
                    if (body.GetType() == (int)swBodyType_e.swSheetBody)
                    {
                        if (IsOpenGeometry(body))
                        {
                            swApp.SendMsgToUser("Selected body is an open geometry");
                        }
                        else
                        {
                            swApp.SendMsgToUser("Selected body is not an open geometry");
                        }
                    }
                    else
                    {
                        swApp.SendMsgToUser("Selected body is not a sheet body");
                    }
                }
                else
                {
                    swApp.SendMsgToUser("Please select sheet body");
                }
            }
            else
            {
                swApp.SendMsgToUser("Please open model");
            }

            return;
        }

        private static bool IsOpenGeometry(IBody2 body)
        {
            object[] faces = body.GetFaces() as object[];

            if (faces != null)
            {
                foreach (IFace2 face in faces)
                {
                    FaceShellType_e shellType = (FaceShellType_e)face.GetShellType();

                    if (shellType == FaceShellType_e.Open)
                    {
                        return true;
                    }
                }
            }

            return false;
        }

        public SldWorks swApp;
    }
}

~~~

