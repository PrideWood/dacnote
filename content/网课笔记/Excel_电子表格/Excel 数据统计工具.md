---
date created: 2024-03-01T14:36:55+08:00
date modified: 2024-03-01T14:37:36+08:00
---
## 1 数据透视表

位置：插入 - 数据透视表

![图片](https://mmbiz.qpic.cn/mmbiz_png/7UIicSplVia1ibkiafLe4WoCaUMicEiaVHr2eGr5kEsBaptG3oibTFsaoZQVoVKU3wdXH2xI1W0kiaS2v0T81KYcDI3sUw/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

透视：直观显示数据背后隐藏的统计信息

**使用方法**：明确问题 - 将要筛选的字段拖入统计表的对应区域（可以直接拖入表格中区域，也可在侧边栏拖动）

![图片](https://mmbiz.qpic.cn/mmbiz_png/ekvzUYML61RVJ2IdUhKEu6syp9mgqfJtDA9xdzuiaK7lFycicfX1AicEkEbzAr6ib2GBlSicGe0zPKSfKzCRzBicgTjw/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/EibQkDyjon1S3elibsEJKicYPQ0s5pm8XECrwDCIyKKRicLyyVFlLee3BlvhvyjeeEN6IrDm8a6qZM5RibCHUVHpeSw/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

**默认统计求和**，右键选中值字段任意单元格，**值字段设置**修改计算类型：

![图片](https://mmbiz.qpic.cn/mmbiz_png/TRLqXel3XJM2D51j0Q3pFTKQF7Znap3zpcmNn1rsBEBRsGmgUOEsRKFYp1I2KMxc9ye3QKBTPDOjx7fxckCtUQ/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

**行/列的多字段分类**

**值的多字段统计**

对透视表进行多级设置，将所需的分级筛选条件拉入同一行/列区域，在侧边栏进行对筛选条件级别调整，在上面的条件更高一级。为了便于数据查看，一般对行字段进行分级。（列字段、值字段都可以添加多项；在值字段可以对同一项数据添加多次，再通过值字段设置更改不同的计算类型）

**透视表中****不能使用自定义排序**：若要对数据进行排序，拷贝数据透视表 - 粘贴为值再进行排序

**日期合并统计**

如果有数据记录为日期而需要统计月份，修改单元格格式使其显示为月份不能被数据透视表识别，需要怎么做呢？

**方法一**：添加本身值为月份的数据，此处引入一个**text 函数**，用来转换日期值为月份/星期：

① 新建列“月份”“星期”

② 选中“月份”列的第一个单元格，插入函数 - 找到 TEXT 函数（也可以直接搜索该函数）

![图片](https://mmbiz.qpic.cn/mmbiz_png/RUfzCfxm9mdYibpSsjAP3Iorfria8JMPOlzB0SB3jbZquSEW5vhSxGJe8NfmPouRLHmR8euSHWSepFQnKf0V6TIA/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

③ Value 选中同一行的日期值 -Format_text 填写所需要的转换的格式代码：如月份为 m，星期为 aaaa。

![图片](https://mmbiz.qpic.cn/mmbiz_png/wjkia5DldzCerqZHBNib9PTAApj3pJkwyUweR3ictYmhYhcW7LrfyEAbqAtBmGJ9x3XPwXQVcOlibmtE6FAibDWcOAA/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

动图演示如下：改为星期同理

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrPr9Qiab2WLSyatCsud9uB5we8amD0LblPcg6Z26zicBRQH1GMxiaH8LuibhVWqSPPibMclpdicAl7D0HnQ/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

以 m 为代码表示的月份在数据透视表中排序可能出现问题，建议使用 mm

（此方法适用于所有电子表格软件）

**方法二**：**右键组合**工具（WPS2016 及之前的工具没有此功能，后续 WPS 版本尚不清楚）

选中数据透视表日期表头单元格 - 右键组合

动图演示：

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrPr9Qiab2WLSyatCsud9uB5wWeLXA72K9okBPHry0OrxNIgFUzFbYiaEicoL8DMSKVL6ZiaMcglaiaw49Q/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

数据透视表**默认对于行、列都进行总计**，如果需要取消总计：值字段任意单元格右键 - 数据透视表选项 - 汇总和筛选 - 取消勾选

![图片](https://mmbiz.qpic.cn/mmbiz_png/jobsiaaOUAgWLIHOqXmOxNB57znx8zckuiap40hRCSho3FjQs6rKbSzmXWPdwqqsyAtic6RvHK98McU0DY9OJuCKQ/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

对报表的筛选（页字段）

把需要筛选的条件拖入报表筛选字段区域即可

![图片](https://mmbiz.qpic.cn/mmbiz_png/TicUswgBZQsEU5ZibO2LnIEgtOzHLmgoe4ic3Qib5YicpjaNmEQFjuiczUK65vXZJGiaMTPajfOT9pPJAhsMkibKXIexAw/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

## 2 分类汇总

位置：数据 - 分类汇总

![图片](https://mmbiz.qpic.cn/mmbiz_png/C7ib8mF3sqvxrOiauEWuGT0LUOvNxQW6JJEb0DSrOXhPuZkZVTGRLY6Ojc0j9RURUzsr8lhCkqJlS4ZddMcpFNLg/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

分类汇总之前需要先进行排序，使得你要分在一类的数据都连在一起。

比如，下图要对各个组别的同学进行分开统计：

![图片](https://mmbiz.qpic.cn/mmbiz_png/2G8tIWZtjqFMPH1vfxiakOHAZpXjmO76ToibTGycWErVlwgTDB9Jk0jtu9iazdqvRKCqL82WFnpzVduOedCtiaKOaw/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/KClKVq3Ht876hvmS31ugQLsJnqUz9x72syj5Y4LxPL5RgHSE8qZVSOSEic6D7bmRSeCGic1Eq0dohLryYg1FmiaLg/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/z0mNCQ1MwYBH6ic3Ull5rHSnbLE0BJDbuzP4VmHvia37fa1XGbYljiaO3LAibYzMAbUNicJJ4Js1puwY6ZlPbCczvjQ/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

左侧数字选择分类级别，括号选择展开/收起数据显示

**取消分类汇总**需要在分类汇总对话框点击全部删除

**分类汇总的嵌套**

和数据透视表可以进行多级字段设置类似，分类汇总的条件也可以设置多个。我们注意到在上上个图中下方有三个可勾选项，第一个选项默认勾选，如果需要对分类条件进行嵌套，则需要**取消勾选**。

分类汇总某一级的结果不能直接复制到其他工作表中，要复制可见数据需要借助定位工具（位置：开始 - 查找和选择 - 定位条件 - 选择可见单元格）

![图片](https://mmbiz.qpic.cn/mmbiz_png/SEVOic5ibAuDqWicNZXvUCiaXTaSjyF2JKfcSUThxq2qwdBukGlDzx8AMnsNYh0svADBdjib26NXTEvftk1bMic5iaFdw/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

## 3 定位工具的更多应用

**定位空行或文本：**

问题：在生成数据透视表的值字段时，默认计算不是求和而是计数，说明想要统计的数值项目里存在空值或文本，此时我们要借助定位工具查找该数据。

![图片](https://mmbiz.qpic.cn/mmbiz_png/z0mNCQ1MwYBH6ic3Ull5rHSnbLE0BJDbu0ekFDk27LykIwA2S2iaxRicwZQk1crog4hAFRgBRX1jfF1X7nLHZibMog/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

在 WPS 中，可以直接选中数据列利用格式 - 文本转数字工具使得需要统计的数据列不存在文本。

**定位图片、文本框等**：定位 - 选择对象（对象即除了单元格之外的所以东西）

不建议平白无故去找对象，不然就会出现封面的内容。

![图片](https://mmbiz.qpic.cn/mmbiz_jpg/mhpgqe0LyrPr9Qiab2WLSyatCsud9uB5wDos2EQ38jo51qX5OzRvjQvic7BIicm9fAP9jEyZ8FdNHgNXGicQKA3uVA/640?wx_fmt=jpeg&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)