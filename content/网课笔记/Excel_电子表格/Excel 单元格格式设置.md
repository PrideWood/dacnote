---
date created: 2024-03-01T14:08:24+08:00
date modified: 2024-03-01T14:18:51+08:00
---

## 几个小技巧：

**报表常用字体**：中文 - 微软雅黑；英文 -Arial
**双击格式刷**可以连续使用，按 Esc 键退出
**斜线表头**：用边框实现
在**单元格中换行**：`Alt+Enter`

## 单元格格式设置

![图片](https://mmbiz.qpic.cn/mmbiz_png/tyicqo99ZRNW10CAo1J5TKuniaSTicb5O8SH9LSCI9qJq57hJAdaCPDb8CVsBiaIHsGKYnIyfJr7Ye5RcMnAVW50FA/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/GiclDhYxtmcQPKvuLnBsmokYqFQS3Y7uPt2ictv0n2SNtbsA5ltKsicO6ShQyDshQd7Jl3XH4GfqPyp4g4xQjtKAg/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

对齐，字体，边框，填充对话框相信你都不陌生，保护一看就会。  

后面是对**数字单元格格式**的详细介绍：

### 1 电子表格使用 1900 起始纪年方式

数字 1 代表 1900 年 1 月 1 日（0 时），此后数字依次 +1，日期向后一天（小数部分也有意义，如 1.5 表示 1900 年 1 月 1 日 12 时），所以**电子表格里的日期实际上也是数字**。

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrNDU4MqbKBqQFkZJNZaonLPhAMtpe63I0TgLibP32ZqKgg6INLEA7TwOo4s3QNqSw0j8TAVopXpVXw/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

单元格**格式的修改只影响数据的显示，不会改变数据的数值**。

### **2** 注意文本格式

文本数字不能进行运算（只能计数：有多少个）、数值统计（如电话号码，身份证号等数字序列）

（默认文本居左显示，且左上角有绿色标记，常规数字居右显示）

![图片](https://mmbiz.qpic.cn/mmbiz_png/jPqq1X4bH73Ox4cnlKqKRX5xs0TD03ibPGdQib6hf0uKGBicoKWMjchXPDibChhyjLpoZakt4sjKRVp8Pq96n4yz1A/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

文本不能直接转变为其他格式；只有先设置单元格格式为文本后再输入的数字内容为文本，如果先输入数字再设置单元格格式，需要对数字重新编辑再回车。

**纯数字**可以使用**错误更正符**里的选项转换为数字

![图片](https://mmbiz.qpic.cn/mmbiz_png/WuMSwF36sfib3icLrBTuu0sTL2prIfM0m17OcZtgl5BUhVicJov8RPOpibmXOL10wa4AlIoFUC4elrbric9MWBcPvKQ/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

**文本格式的日期**修改为常规格式

菜单栏【数据】-【分列】选项卡 - 在第一步对话框，勾选【固定宽度】- 第三步对话框勾选日期：（WPS 开始菜单栏里的格式选项卡提供有文本直接转数字的工具）

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/qnyhqPG3VDyaeRvORO0879gDWFCgM6fghxQnyJuC0OvE7STJpb2JjeX7fsRYFXB0PJFmzd99m5NcFBjPTon8LQ/640?wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrNDU4MqbKBqQFkZJNZaonLP0DvjSatP0FDuO0vuXxdOkKkQowYlj4ISXAq1RyPibvwOpmhfekibN5hQ/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

电子表格只能精确到**大数字的前 15 位**（足以满足工作需求）

### 3 自定义数字单元格格式

![图片](https://mmbiz.qpic.cn/mmbiz_png/srkHbOwrV1XMK5ibnkdX3C1icyJG4VySQ3YKVdwm1iakVDby7ORFUMNExpN8lHdtYeh4aFFoCvQva6kiaungohxgOg/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

类型框中输入所需要的格式的代码：

日期的输入：`y` 代表年（year），`m` 代表月（month），`d` 代表日（day）

**年月日顺序可以任意调换，分隔符号也可按需变化，可以只保留显示年月日其中一项，字母个数不同显示格式不同，**

**例**：若单元格中日期显示为 2020/2/27，我们看到它的类型是 yyyy/m/d，现在我们对它进行修改，请观察示例中的显示变化

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrNDU4MqbKBqQFkZJNZaonLPiazdbUzpV9PybFoxoGJAcRAy2bSbPQpDCy4wn1mSbib2uA8NjbwYfecg/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

（看了前面的内容相信你已经明白为什么当删除完所有符号，日期变为数字）

上面的给出的是显示年月日其中一项，可以根据需要自由组合（显示年月，月日，年月日都显示，日可以是日期也可以是星期），根据需要选择用“/”或“-”分隔，如：

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrNDU4MqbKBqQFkZJNZaonLPv1NLoqDQ0ydUBQt16dHBjRuVE2PdSwpADQ4UHFKiadI1PiaiaOmlKVcMA/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

要求**输出中文“星期”时，需要用 `aaaa` 替代 `d`**，

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrNDU4MqbKBqQFkZJNZaonLP2PjCcN0RicFgibwqeFRGiaI0JQqdmHMiaqSyGDgGzfHbcoyHoeOfgkNkSw/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

相信你注意到了 `aaa` 表示“星期 X”中的“X”，所以在 `aaa` 前输入 “礼拜”“周”可以显示为“礼拜 X”“周 X”

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrNDU4MqbKBqQFkZJNZaonLPTb9ibwlicHeSb7zPDwrWjkB9G4zugW3zaeOI7czZaRURl2o7icJRNMNOA/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

同理可以用这种方法添加汉字“年”“月”“日”等

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrNDU4MqbKBqQFkZJNZaonLPl9CtHcchZnzicEpFNXwaCAvYkRW7F9tRibcD0bwGSWdtAoZfzY1FkVjQ/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)  

既然能加汉字，当然可以对数值**添加单位**啦。如我们需要对某个表示金额的单元格添加单位“元”：（一般数值的类型均为 G/通用格式，G：general）

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrNDU4MqbKBqQFkZJNZaonLPFd7WbExiaFV84n9GP5uC1zkJyZsoePw5nr9gsZXRxj73IKVpAqFDvaQ/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

注意：**标准的写法应该给汉字添加双引号**，不加的话系统会为我们自动加上。

### 4 占位符 `0` 和 `#` 的应用

（上面提到的 y, m, d, a 均为占位符）*

常用 `0` 补齐小数点后不足需要精度后的位数，一般不用 0 占高位

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrNDU4MqbKBqQFkZJNZaonLPHpM30N1akVbqT4Mx2jKZkeXmfAwUfVGUMXCnYItsvpZLmytyV4ZzWA/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

利用 **`#` 占位添加千分位分隔符**

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrNDU4MqbKBqQFkZJNZaonLPO0Wpg5zBdukibpp0AMKF4icTxkQmqUl6ialzt0OE6LdkUaVyGoHFLyMHg/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

上面两者可以**组合使用**

**注意：`#` 只在整数部分起占位作用，如果整数部分为 `0`，则不显示，因此整数部分的最后一位（个位）要用 `0` 表示，防止表格中的数据存在 0 或者纯小数。**

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrNDU4MqbKBqQFkZJNZaonLPibNwpp9foYy5ib0qyHDvCM8uZibW5NfWObRIQ9MpKEJS9eCakKncng0fw/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

**“隐藏”单元格**：保留数据但不显示

![图片](https://mmbiz.qpic.cn/mmbiz_png/SQ5c5gZo0ibYxOQicTFlNUFFiayL3V76RAQoMpETgG57mMj65rS9FzsNLnTc0mGj2a3ibEysXKDCwlLvUSAP3SmQfQ/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

只需要搞清楚这里分号 `;` 即可，这里的**三个分号分隔出的四个区域分别表示正数显示格式，负数显示格式；0 的显示格式；文本信息显示格式**，所以只需要清空这四个区域中的内容即可隐藏单元格内容，不影响引用该单元格的运算，数据还在只是不显示了而已。

以上方法基本能满足所有应用场景了，至于类型中更多符号的意思，有兴趣的话再去查查吧~