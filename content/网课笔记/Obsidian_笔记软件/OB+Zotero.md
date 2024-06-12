#### 28 OB&Zotero 1/4 搭配 Zotero 实现免费跨平台知识管理 

Zotero 并不是需要读论文的研究人员才需要的工具
插件：Citations
原理：通过 Citations 打开 Zotero 里的数据存入 Obsidian 里（即转为 MD 文档）
步骤：
1. Zotero 导出 CSL-json / BibLaTeX
2. 在 Citations 插件设置页设置刚刚导出的文件格式、路径、导出的 MD 文档存放文件夹、需要导出的内容模板等
3. 命令行调用 Citations 插件
弹幕：Windows 下按住 `shift` 右键复制路径且需要去掉引号
OB 使用到的 Citations 插件的下载地址： https://gitee.com/whghcyx/obsidian-plugin/blob/master/plugin/obsidian-citation-plugin.zip

#### 30 OB&Zotero 2/4 使用 Better BibTex 实现同步更新

1. 给 Zotero 安装插件 Better BibTex
插件的下载地址： 链接： https://share.weiyun.com/azpmjkiX 密码：dxhfb6
2. 在 Zotero 导出时选择 Better BibLaTeX，出现新的复选框 Keep updated，勾选
3. 重复第 28 集的设置，如果已经设置过不需要重新设置
提示：Zotero 因使用火狐内核，插件安装完重启方可使用。在评论区看到有不少同学表示即使使用插件修改后（比如增添了笔记）的.bib文件中并未更新，实际上**只有在新增或者删除另外一个新文件（比如一条笔记，而不是在原有的笔记上修改）才会更新**。

#### 32 OB&Zotero 3/4 OB 如何使用 Zotero 内置的 PDF 阅读器中留下的高亮等

情况一：在 Zotero 内部设置使用内部 PDF 阅读器打开 pdf 文档，可以直接记录 Zotero 条目子笔记
情况二：使用其他 PDF 阅读器需阅读借助 Zotfile 插件，（Mac）做好高亮后保存，在文件上右键出现 Manage Attachments（管理附件）-Extract Annotations（提取注释）
Zotfile 插件下载： https://share.weiyun.com/azpmjkiX
注意：第 30 集实现的同步只是 Better BibLaTeX 文件的同步，OB 里的 Markdown 文件还要手动更新。使用外部阅读器导出的高亮或者批注是含有链接的，可以定位到对应的位置。

#### 42 OB&Zotero 4/4 Zotero 的 MdNotes 怎么和 OB 一起用

![Pasted image 20240113161332](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/Pasted%20image%2020240113161332.png)
本集内容还是以实操为主，跟着 Johnny 做一遍应该就会了，没太多可记的。
提醒：
Mdnotes 的两种输出模式
- Single file
- Split files

#### 43 Zotero 插件 MdNotes 的模板使用介绍，同 OB 结合使用

接上节，无太多内容可记，看了一遍目前对于本人没有合适的应用场景
Jonny 的这种思路真是属于产品开发者的思路，这几节的内容应用场景也可能不大。最终带来的便捷在阅读量不大的情况下也不太能凸显，大概可以总结为：将 OB 里的笔记和 Zotero 里的 PDF 原文对应，其实在看文献时复制粘贴手动在另外的文档里写笔记也不是太麻烦，尽管不能定位原文位置，但是相信也很少有文献值得反复查看，真正重要的文献单独整理在一起多次阅读就是了，或者在摘录时养成记录页码的习惯也费不了太多事。