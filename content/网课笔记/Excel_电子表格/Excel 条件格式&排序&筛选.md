---
date created: 2024-03-01T14:19:44+08:00
date modified: 2024-03-01T14:22:04+08:00
---
**关于颜色的几个提示：**

- 深色背景上的字通常调整为白色 (最清晰)
- 活用颜色（字体色与背景色一致可以隐藏字体内容）
- 一个表格中不要出现太多种颜色

**找到重要数据**

【开始】选项卡：

![图片](https://mmbiz.qpic.cn/mmbiz_png/icQbPzwfXiakFOlNBWD2GicyLohNlw1gUOvRf1aqtpSibhwwtSHUDX5QmnLDBfMN7VAj2OyFytucjib2cxldXR7uSRQ/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

## 1 条件格式

![图片](https://mmbiz.qpic.cn/mmbiz_png/9cD3Ux0TeBv7qpsQlDAYia1PruGibaU7nJAvnJSthIN6uOa8sIx2xWrOxJGyBsE4XUJWNEY74eAFUIOXgrZD8gibQ/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

**应用场景**：  

- 标记某个范围的数据
- 找到重复的项目
- 使用图形增加数据可读性

**数据条**长短用来比较；颜色用来区分
**图标集**只用于区分，在编辑规则里设置区分的条件
**色阶**（用途少）：有比较也有区分（常用来表示温度等），不同颜色用于区分、深浅用于比较

**关于数据条的使用提示**

调整坐标轴位置：管理规则 - 选中 - 编辑规则 - 负值和坐标轴 - 坐标轴设置 - 单元格中置（无）

新建规则 - 使用公式确定设置格式的单元格（见后续笔记）

## 2 排序

选中需要排序的一列中任意数据的单元格 - 排序

**出现空行**：系统认为空行上下是分开的两个表格，只对选中的一部分排序

解决办法：选中所有数据 - 自定义排序

**自定义排序**

功能：改变排序依据；可以添加多个条件；（是否勾选“数据包含标题”影响排序结果）

**汉字**默认以音序排序

要根据汉字一二三顺序排列：

自定义排序 - 次序：自定义顺序（自己指定顺序，此时系统中就增加了自定义的序列，利用填充柄可以自动填充）

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrOAcaPCUwkJvqaMAtxgFib6JuSMoRCoc3pKaiaPNlxsTcO1UiczBYKolCBsbdOegia83dIFmianrB2Lu0Q/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrOAcaPCUwkJvqaMAtxgFib6JBhy9nyzOFgYNc0d2raia3KLck0hJibBUsAOp1gPHickfPe7GeP9rjiaHvA/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

## 3 筛选

![图片](https://mmbiz.qpic.cn/mmbiz_png/mfBPXwy797ULoMoMbaBsztQxTg7s1xiaTgUtbPKQ9kiboFaEtZ3b4pBbUBPYcctf91sexMEsoNtCSOkQhniclZjew/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

未筛选（展示全部数据）显示为倒三角状，已筛选显示为漏斗状，且左侧行标号变色；若需要取消全部筛选在菜单栏里选中清除

![图片](https://mmbiz.qpic.cn/mmbiz_png/gLxa9I0nnVf3qNVWIyEtXRlqch7JE0lzXWXyrfHAnURL5SQYkvfCA6QYvPlptBcfjPLzWWBR5KxzqRNGF1I90A/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

注：筛选后求和使用的是 subtotal 函数而非 sum 函数

WPS 高级筛选：可以做逻辑关系为“或”的条件，工作场景应用不多：

在空白处单元格建立筛序条件（条件区域，带表头），同行条件的逻辑关系表示“且”，不同行表示“或”

利用高级筛选生成不重复值列表

## 实践：制作个人成绩单（包含表头和个人成绩数据）

传统思路：复制粘贴表头、个人成绩各 n（班级人数）次

利用**今天所学**：

复制表头 - 为成绩行和表头行分别添加序列（表头行的数值在两个成绩行之间，同理可以添加空行）- 排序

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrOAcaPCUwkJvqaMAtxgFib6JVia3gLY6iazgmia3vlibJg97ffic6Y9Nian1Td3iaHDcbJ0kaplUA59Ca2o9A/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrOAcaPCUwkJvqaMAtxgFib6JpnK6oyZ5HFQNudFThYR6lbbicWIMQSQcY9o6uGtDpFliaRibw02kFOsDA/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)