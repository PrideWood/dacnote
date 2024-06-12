#### 12 使用 Pandoc 插件，飞速制作 PPT

资源下载地址： 链接： https://share.weiyun.com/OKNoCJsF 密码：6ybttp 包含，Pandoc 的 windows 和 Mac 安装包 以及最新的 Obsidian Pandoc 插件
1. 安装 Pandoc 软件和 obsidian-pandoc 插件。
2. 设置 obsidian-pandoc 插件路径：设置页面找到 Pandoc path，注意路径前面不要有空格
OB 目录中不会显示 PPT 文件，需要用电脑的文件资源管理器打开，最后套用模板。

#### 33 从 OB 导出 Word 或 PPT

联系第 12 集
OB 设置 - 文件与链接 打开检测所有类型的文件 保证导出的文档名可以在 OB 中显示
以设定好的模板样式导出:
1. 给空的 ppt, word 设置好样式
2. 在要导出的笔记添加代码，该代码中的文件路径即为上一步中的文件路径

```
--reference-doc=/path.尾缀
```

3. 完成 Pandoc 插件相关设置（尤其是 Extra Pandoc arguments），导出

#### 51 Pandoc 输出封面页，Markdown 空行去除，MD 美化，Shell Commands 插件

Q1: pandoc 将 markdown 转为 docx, 想把 heading 作为标题居中
A: 在 frontmatter 写上 title, subtitle, author 等属性，同理也可导出为 PPT
例如

```
---
title: 这是标题
subtitle: 这是副标题
author: 佚名
---
```

PPT 中的分栏页面，如下图效果
![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240114120457.png)
需要在 pandoc 里写相应的语句，会自动应用分栏模板

```
::: columns
::: column

1. 我会如何给你上课
2. 认识试讲
3. 学科知识的准备
4. 认识教案
5. 如何才能写好教案

:::
::: column
6. 我会如何给你上课
7. 认识试讲
8. 学科知识的准备
9. 认识教案
10. 如何才能写好教案
:::
:::
```

Q2: 如何清除空行
A: 如果都是多于空行，用文本处理的那个网站；建议使用插件 Markdown Prettifier, 该插件会保留必要的空行
评论区
> Markdown prettifier 这个插件作者已经不维护了，他推荐使用这个插件：obsidian-linter。*@lesserror-*

插件 Shell commands 可以保存命令行的很多命令，比如：导出 ppt 到不同的模板，给每种模板都保存一个命令行；不同的操作系统下因为命令代码有所不同都可以一次性保存好。