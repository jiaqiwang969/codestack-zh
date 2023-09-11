# 项目总结 (2023-09-11)

这个项目是关于GPT辅助SW二次开发插件设计的。通过langchian嵌入solidworks文档，实现专家知识。以下是项目的主要步骤：

1. 整理codestack网站上的所有文档，并将其转化为docusaurus类型的网页文档;
2. 自动将文档翻译成中文;
3. 利用langchain将文档进行处理和转换。

该项目的目标是提供一个方便且高效的方式来利用GPT和solidworks进行二次开发，并将专家知识嵌入到插件中。通过这个项目，我们可以更好地利用现有的solidwork API，实现二次开发和自动化。

如果你对这个项目感兴趣，欢迎参与和贡献！


- [x] 1. 建立docusaurus网站
- [x] 2. 测试langchain转化文档为向量库
- [ ] 3. 通过GPT-translator实现自动化翻译
- [ ] 4. ..


# python代码实现功能
copy_md_files.py: 将docs文档中的markdown文档提取出来；
push_comments.py: 生成可以生成上传/gh命令的python文档；
push_comments-bash.py: 实现自动化翻译上传/gh命令


# 执行merge命令
```
for pr in $(gh pr list --json number --jq ".[].number"); do     gh pr merge $pr -d -m; done
```



```
616: gh issue comment 1 --body "/gt python-auto/docs-md/visual-basic_algorithms_fso_get-files_index.md python-auto/docs-md-zh/visual-basic_algorithms_fso_get-files_index.md simplified-chinese"
```



# 要求
安装 gh poetry nixos-shell 
