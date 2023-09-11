---
标题：SOLIDWORKS宏以在新配置中创建和抑制特征
说明：该宏使用SOLIDWORKS API为特征树中选择的所有特征创建新配置，并在相应的配置中逐个抑制它们。
图片：sheet-metal-bends-selection.png
标签：[特征，配置，抑制]

该宏使用SOLIDWORKS API为特征树中选择的所有特征创建新配置，并在相应的配置中逐个抑制它们。

如果需要在配置中表示模型的某些历史数据，该宏将非常有用。

## 注意事项

* 配置作为活动配置的派生配置创建
* 每个配置以特征名称命名
* 特征按照选择的顺序进行处理
* 在相应的配置中，每个特征及其之前的所有特征都将被抑制

## 使用案例

### 金属板弯曲

该宏可用于表示金属板的弯曲步骤。在这种情况下，每个配置将表示弯曲步骤。

* 将金属板零件设置为展平状态
* 按照*Flat-Pattern*特征下的顺序选择展平弯曲

![金属板展平弯曲](sheet-metal-bends-selection.png){ width=350 }

* 运行该宏

结果将创建每个弯曲的子配置，表示弯曲步骤：

![配置中的金属板弯曲步骤](sheet-metal-bending.gif)

参考[SOLIDWORKS API动画配置](solidworks-api/motion-study/animate-configurations/)的示例宏，以使用SOLIDWORKS API对配置进行动画处理。

{% code-snippet { file-name: Macro.vba } %}