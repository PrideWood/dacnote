---
date created: 2024-03-01T14:57:31+08:00
date modified: 2024-03-01T15:13:17+08:00
---
## VLOOKUP 函数基本应用

搜索表区域首列满足条件的元素，确定待检索单元格在区域中的行列号，再进一步返回选定单元格的值。默认情况下，表是以升序排序的。

`VLOOKUP(lookup_value,table_array,col_index_number,[range_lookup])`

**巧记：到隔壁办公室找老张，把他水杯拿过来。**

四个参数：

① 需要查找的项目；
② 查找数据源（选区）；
③ 查找结果在选区的第几列；
④ 精确匹配（0/FALSE）/模糊匹配（1/TRUE）

**必须保证查找列和结果列且查找列是选区的第一列。**

本节函数处理数据比较多，直接采用王老师的演示文件进行演示，如若只看笔记不能理解，同学可以直接通过下方链接获取本节数据表格文件链接自己实践一下：

https://pan.baidu.com/s/1Cmqv-byc2iekTSLSGOkLjw

提取码：pcs2

## 例 1. 根据客户名称查找公司名称

数据源如图所示（就是很多数据，每一行对应一条项目，图片未显示完全）

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOsnGM2JO5RQprVACCbALDtNcHJtp30wRibfABMZmucxAljvTSXicWUo4Bmfw0m6JXqB3C98vw23wUA/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOsnGM2JO5RQprVACCbALDtF1yxpShXdG5oydzh3tdSUvs1Jk4RnmvKbLLCYtiad3Z6ySiauXkhAP9w/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)  

## 例 2. 建立可动态变化的客户信息表

利用 VLOOKUP 函数建立一个如图所示的可动态变化的客户信息表

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrOsnGM2JO5RQprVACCbALDtPMJOTYW7CNGsfEEI2BuB6tGLBuFT9XGdtaYUg69qKzUCtrZ8H0qQoQ/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

还能记得如何**设置下拉列表**吗？

数据 - 数据验证 - 序列

**使用通配符进行查找**：

在实际工作场景中，由于输入信息的不规范（例如公司名称是否为全称：腾讯/深圳市腾讯计算机系统有限公司），会导致使用 VLOOKUP 函数查找时出现错误：

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOsnGM2JO5RQprVACCbALDtjNNWrP5iaKCvcXh4ibSotxXI4lO5jcNicKHlIBIicbQBicjrzy8phacBS3A/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

腾讯/深圳市腾讯计算机系统有限公司 差在哪呢？

很明显是划线部分，用**通配符 `*` 代替**这些部分（前面的笔记说过啦）放在公式里就行了。

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOsnGM2JO5RQprVACCbALDt93ib0osCl1IGek38wOVj6Kqxl8SgVoF0rx4sI8GjdWcnC9fQiaXO0HMw/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

上面的例子都使用的是精确查找（因为一条项目信息之间是对应的，不允许有差错）那**模糊查找**有什么用呢？

**注意**：模糊匹配需要对数据**升序排序**。

这里说的近似与模糊在逻辑上只能是针对数值来说，且会**优先查找小于等于查找值的结果。**

给出例子便于记忆：根据年龄匹配相亲，28 与 32 相对于 30 的近似程度一致，优先推荐比男嘉宾年龄小的女嘉宾

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOsnGM2JO5RQprVACCbALDtRvP0cRsBw3dlzHicVr9JrPfkFXgA1nmm4Cyia1ZsxbvVsW6B7hNHPV5A/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

## 在商务场景里的应用

### 计算提成（例题场景，实际采用这种计算方式并不科学）

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOsnGM2JO5RQprVACCbALDttJubyYmkENDBceEKEfdKefFSXibgibKmeiamwDQb5IuiadHjAKqHk4fB0A/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

注：

① 一般商务场景的等级划分不会写取值区间只会写出等级下限；

② 注意在选中非整列数据时对选区使用绝对引用。

### **计算个人所得税**（个税）

传统计算方法：计算超出部分每一段应交税额相加（**分级累进求和**）

引入速扣数（使用最高税率多扣的部分）：根据应纳税所得额与对应税率直接计算

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOsnGM2JO5RQprVACCbALDt0pvzXSCB5IfSlpqLc4E2CRJiac7iawWoW635yL2rSgO1Yaqg7ySTUN9Q/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

如果税前月薪达不到起征点呢？即个税为 0，使用前面学过的 IFERROR 函数使结果输出为 0 即可。

**数字格式问题**

之前提到文本格式的数据不能直接进行运算（不能使用公式），所以要将文本格式的数字转化成常规格式等。

但往往在处理问题时有的数据只可读不能编辑，则需要我们**在公式里对数值的格式进行转换**。

可以使用**运算符强制进行数据类型的转换**

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrOsnGM2JO5RQprVACCbALDt3jvAHdCfwUPyoibKnA5HMQicrxyhcRbQhOZAbsREyiaTLZrfsXiaTh771A/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

如何数值转文本？看下图

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOsnGM2JO5RQprVACCbALDtrFUg6mb3clu6GcVUQoHiaB4pv1yLSvOCAzOFI6dk3aWWfYhogRm1VZw/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

应用：

根据数值查文本（文本查数值同理）

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOsnGM2JO5RQprVACCbALDtbu5TtCWk6GvGhWWDHSYLrdIZOiajKibFTgvARULOicUVg6nFmWrWHZJtQ/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

如果数值文本混在同一个表里呢？

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOsnGM2JO5RQprVACCbALDttbkoc5JOlWxmUCMyAhRrZSQV7FwkicicGormHzXKF9mTsZiaIErCI5RMg/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

提示：先写 VLOOKUP 再写 IFERROR 防止函数名写错难以排错。

VLOOKUP 不能实现右侧查找值找左侧结果（选区第一列必须是查找列）

如何解决这一问题呢？

① 原始数据列顺序重排

② 不能进行更改列顺序，借助**MATCH 与 INDEX 函数**

（事实上，MATCH 与 INDEX 函数早于 VLOOKUP 且功能强大但是后者更便捷。）

## 回到本节例 1：

如果要根据公司名称查找客户 ID 如何操作？（数据源表中客户 ID 在左侧）

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOsnGM2JO5RQprVACCbALDtcOuReas9eo6MmqFPvpRz4w7Rr2rygfbKaDVDiatWUwNNDkjpNf397EQ/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOsnGM2JO5RQprVACCbALDtSgT8agc2mVRY4ANNHF7QYo9ottrEicbNozjfel5cHs9oCEYApBh2Ylw/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOsnGM2JO5RQprVACCbALDt4ekibLahyxRvx3w9Uibf8H5k87UWJJhaQo6BqVUrKPCFgvbzyofR2ibDA/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)