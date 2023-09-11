脚本使用SOLIDWORKS API根据指定的参数从输入参数生成模型

* 创建两个文件并将以下代码粘贴到文件中

## model-generator.ps1
{% code-snippet { file-name: model-generator.ps1 } %}

## model-generator.cmd
{% code-snippet { file-name: model-generator.cmd } %}

下载[模板模型](template.SLDPRT)并将其保存在与上述两个脚本相同的文件夹中。

这是一个具有3个驱动参数（宽度、高度和长度）的模板模型。

![带有参数的模型](model-parameters.png){ width=350 }

此模型将由脚本修改并保存为新文件。

* 启动命令行并执行以下命令

~~~ bat
[model-generator.cmd的完整路径] [输出SOLIDWORKS文件的完整路径] [宽度] [长度] [高度]
~~~

结果将生成文件，并在控制台中直接显示进程日志：

![控制台中报告模型生成进度和结果的消息](console-output.png){ width=450 }

模板文件不会被修改，生成的模型将带有更新的参数保存。

![应用参数的生成模型](model-result.png){ width=350 }