---
标题：使用SOLIDWORKS API从所选组件中读取特定配置的切割清单属性
说明：使用SOLIDWORKS API，通过VBA宏从装配体中所选组件的切割清单中读取所有属性的示例
图片：cut-list-properties.png
标签：[切割清单属性，组件]
---

![切割清单属性](cut-list-properties.png){ width=550 }

此VBA宏示例演示了如何使用SOLIDWORKS API从装配体中所选组件的所有切割清单元素中读取和打印所有自定义属性。

切割清单是从组件的相应引用配置中读取的。

结果以以下格式输出到VBA编辑器的即时窗口中。

~~~
CS-02-1 (A)
    Sheet<1>
        外包络盒长度：150
        外包络盒宽度：50
        钣金厚度：0.74
        外包络盒面积：7500
        空白外包络盒面积：7500
        外切长度：400
        内切长度：0
        切割数量：0
        弯曲数量：0
        弯曲补偿：0.5
        材料：未指定材料
        质量：5.52
        描述：钣金
        弯曲半径：0.74
        表面处理：未指定表面处理
        总成本：0
        数量：1
~~~

{% code-snippet { file-name: Macro.vba } %}