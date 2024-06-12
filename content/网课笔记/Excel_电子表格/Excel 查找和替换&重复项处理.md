---
date created: 2024-03-01T14:45:48+08:00
date modified: 2024-03-01T14:48:24+08:00
---

## 查找和替换

![图片](https://mmbiz.qpic.cn/mmbiz_png/edvmrFrkzzPhZicFYYDF4vI7Z0eaNtRb9bd5aFrIphZ1sCG1AAlB3otzaj4kOUMcuCvVUeBesK70dibibBWPuEKqA/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

可以先选定范围再做替换（防止替换了不需要替换的内容）：选定某列（行）

**问题**：现有表格性别一栏中有的内容为“男”、有的为“男生”，现在要统一改为“男生”该如何操作？

如果直接替换“男”为“男生”，因为“男生”中也包含“男”字内容，会导致变成“男男生”。

**解决方法**：查找和选择 - 替换 - 展开选项 - 勾选**单元格适配**（即要查找的内容为单元格仅包含的内容）

![图片](https://mmbiz.qpic.cn/mmbiz_png/7ibgzicMo4PmLgXANre9ibumSibvCO060iaDicm8X9pX9jDQ07rjlR6iblTAlhpx8oGdCcmBb1ZopunicBaeIrR180oUHA/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

在上图中我们注意到，替换还可以对单元格**格式进行替换**。

注意：替换工具有记忆功能，如果要进行两次不同内容的替换，要对前一次的替换的记忆进行清除。

### 使用通配符

**`*`（星号）**：表示任意个数的字符

**`?`（英文问号）**：一个 ? 代表一个字符

例如我们要把所有王姓的同学替换为“老师的亲戚”：

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrMqESe1rPh4Xspa2euxEdiauHibs9pmCZjpzhrzEcffKPEOLpWwZjKwkVfyXa7xM5ibYKhYaLjiasYZmQ/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

**问题**：如果要只替换表格中含有通配符的单元格内容该如何替换？

**解决方法**：在要被当作文本的 **? 或 * 符号前添加~（数字键 1 左侧按键）**

![图片](https://mmbiz.qpic.cn/mmbiz_gif/Hfh61fSZadiaJKKamCziceVUjOFVGMmmk2qPTykvEQNMHiaibdV5W3jQwhg4icG3yYYuKibcNQia1XLP8Xy9YM83fCkicA/640?tp=wxpic&wxfrom=5&wx_lazy=1)

## 重复项处理

设置**突出显示**重复项  
**条件格式**- 突出显示 - 重复值

WPS 中数据 - 高亮重复项和条件格式设置是一回事

**删除重复值**

数据 - 删除重复值：此操作保留第一次出现（排序更前）的数据。

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/mhpgqe0LyrMqESe1rPh4Xspa2euxEdiauB8PWxNyNtNrtzKV2nutnJH7ECdaib7k1efh3j9tZ5jSa2ZJBzicovVKQ/640?wx_fmt=jpeg&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

复制原数据进行删除重复项操作可得到**唯一值列表**。

WPS 中的拒绝录入重复项即**数据验证**中的功能（紧邻删除重复值右侧）

![图片](https://mmbiz.qpic.cn/mmbiz_png/E6ysQCASR4fvGnEib7V0gGOJf5Ybebu1Vka1spEVU6RrdOrdLwjqXqZKwajmyxejqXndk7dPTo6aTGgvfwpbXEA/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

输入信息：可以在选中单元格式显示输入内容提示；

出错警告：即输入非法信息后弹出对话框提示；

三个样式：停止，警告，信息，选择停止则不能录入非法信息。

设置 -**序列**

用来设置单元格内容下拉框，如性别一列我们设置男、女两个选项

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrMqESe1rPh4Xspa2euxEdiauQ5N2g3ArmSkicVU1cyQOoeQzQsVexcJLTp7kNYsCjKRicJANSQ6hcGsw/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

设置来源分隔时必须以**英文半角逗号**分隔，也可以在表格空白区域输入所需要的填充的序列，直接引用位置即可（一般新建一张工作表选定一列表格区域作为来源，方便未来在下拉选项需要增多时直接在该列空白区域内添加选项信息。

![图片](https://mmbiz.qpic.cn/mmbiz_gif/Hfh61fSZadiaJKKamCziceVUjOFVGMmmk2qPTykvEQNMHiaibdV5W3jQwhg4icG3yYYuKibcNQia1XLP8Xy9YM83fCkicA/640?tp=wxpic&wxfrom=5&wx_lazy=1)

## 表格公式基础

绝对引用（快捷键 F4）与相对引用，混合引用（后续讲解）

公式反推：借助单变量求解功能：数据 - 模拟分析 -**单变量求解**

![图片](https://mmbiz.qpic.cn/mmbiz_png/2GAqLtk4LGDpcfyFEY5HkYJCUTQbI4ZmjiafQUkm7qgIVLnCYHWgLzPuC2rMu7nhsPOGd1K0t2ibRZVcHonVicaibA/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)