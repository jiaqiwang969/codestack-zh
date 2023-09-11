---
title: SOLIDWORKS API对象模型类层次结构图
caption: 类图关系
description: SOLIDWORKS API对象模型中类和接口之间关系的详细解释（类图）
image: class-diagram.png
labels: [层次结构, 类, 模型]
order: 1
scripts:
    - "scripts/svg-pan-zoom.min.js"
---
下面的图表显示了SOLIDWORKS API对象模型中接口之间的关系。这不是一个完整的类层次结构，而是对最常用的方法和接口的表示。

图表是交互式的，可以使用鼠标滚轮进行缩放和平移，也可以使用鼠标右键或左键进行平移。右下角的导航控制可以进行缩放和平移，还可以自适应缩放。

![控制框](control-box.png)

所有的方框和箭头都可以点击，会跳转到有关特定方法、属性或接口的信息页面。

![打开链接](open-link.png){ width=250 }

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

## 图例

<img src="legend/init-box.svg" alt="初始化"> 表示程序的入口点。可以是类的构造函数、连接方法、宏的入口点等

<img src="legend/interface-box.svg" alt="接口框"> 表示SOLIDWORKS API的接口（对象）

<img src="legend/cast.svg" alt="转换"> 表示通过直接转换（查询接口）在接口之间的关系

<img src="legend/method-property.svg" alt="方法或属性"> 表示通过方法或属性在接口之间的关系

<img src="legend/group.svg" alt="组"> 表示一组接口

<img src="legend/selection-interface-box.svg" alt="选择接口框"> 表示SOLIDWORKS用户界面中可选择的接口对象

<img src="legend/selection-box.svg" alt="选择框"> 表示所有可选择对象的占位符（即具有蓝色背景的接口）

<img src="legend/etc-box.svg" alt="其他框"> 表示此组中的其他接口的占位符

<img src="legend/etc-box-wildcard.svg" alt="带通配符的其他框"> 表示此组中的其他接口的占位符。接口名称将与通配符匹配