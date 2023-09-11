---
title: Get the total length of segments in selected sketch using SOLIDWORKS API
caption: Get Total Length Of Sketch Segments
description: C# example to calculate total length of all non construction geometry sketch segments in the selected sketch using SOLIDWORKS API
image: sketch-total-length.png
labels: [sketch,length]
---

![所选草图线段的总长度](sketch-total-length.png){ width=450 }

这是一个C#示例，用于计算使用SOLIDWORKS API在所选草图中所有线段的总长度。计算中将排除构造几何线段。

~~~ cs
using SolidWorks.Interop.sldworks;
using SolidWorks.Interop.swconst;
using System;
using System.Linq;

namespace CodeStack
{
    class Program
    {
        static void Main(string[] args)
        {
            var app = Activator.CreateInstance(Type.GetTypeFromProgID("SldWorks.Application")) as ISldWorks;
            app.Visible = true;

            if (app.IActiveDoc2 != null)
            {
                var feat = app.IActiveDoc2.ISelectionManager.GetSelectedObject6(1, -1) as IFeature;

                var sketch = feat?.GetSpecificFeature2() as ISketch;

                if (sketch != null)
                {
                    var segs = (sketch.GetSketchSegments() as object[])?.Cast<ISketchSegment>();

                    if (segs != null)
                    {
                        var totalLength = segs.Where(s => !s.ConstructionGeometry).Sum(s => s.GetLength());

                        app.SendMsgToUser2($"Total length of segments: {totalLength} meters", (int)swMessageBoxIcon_e.swMbInformation, (int)swMessageBoxBtn_e.swMbOk);
                    }
                    else
                    {
                        throw new NullReferenceException("No segments in the sketch");
                    }
                }
                else
                {
                    throw new NullReferenceException("Select sketch");
                }
            }
            else
            {
                throw new NullReferenceException("Open document");
            }
        }
    }
}

~~~

