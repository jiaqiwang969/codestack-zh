---
标题：计算旋转变换以使组件与方向对齐
说明：这个VBA示例演示了如何使用[SOLIDWORKS API的IMathUtility::CreateTransformRotateAxis](https://help.solidworks.com/2017/English/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.IMathUtility~CreateTransformRotateAxis.html)来旋转组件并将其面的法线与线性边的方向对齐。

作为前提条件，选择装配中第一个组件上的平面面和第二个组件上的线性边。第一个组件不能被固定，并且不能有任何配对关系。结果是第一个组件被旋转，使其法线与边的方向共线。组件围绕原点旋转。

## 解释

为了以预期的方式转换组件，需要计算其变换。为此，需要找到旋转的原点、旋转向量和角度。

首先，我们创建面法线和边方向的向量。需要应用组件的变换以将向量表示在相同的坐标系中。这两个向量之间的角度是变换的所需角度。

为了找到旋转向量，需要找到法线和方向的垂直向量。可以通过求叉积来实现。

最后，旋转点是组件的原点变换到装配坐标系中的点。

![旋转变换参数](rotation-transform.png)

{% code-snippet { file-name: Macro.vba } %}
