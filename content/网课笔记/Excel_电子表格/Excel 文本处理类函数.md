---
date created: 2024-03-01T15:14:31+08:00
date modified: 2024-03-01T15:18:54+08:00
---
## 使用分列工具

位置：数据 - 分列

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMCzeZjs3KguU2ia1jaydGxz06kTvLYpccHcYEml55btOLCb0iaCSzuianww/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

1. 按**分隔符号**进行分列：文本文档中的数据转换成表格

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMCJcyXhWibg3HwYFFjcUXDobuW3RVALZicwUYyLLSz1WJRxhOWajCnQfBg/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

复制所有文本数据 - 单击单元格进行粘贴（双击会将所有内容粘贴在同一单元格中）

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMC1h18jSyVWtbOpKVa1w2uRpepkNPxl1gqZQicqpEu27rIruaYDHu3BhA/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

可以看到原本换行的内容也会自动换行，但同一行的内容会显示在同一单元格中；

继续：选中数据所在列 - 数据 - 分列 - 文本分列导向对话框

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMCQIgRHFGib7FSFrclsH3x2QHEZXk0vRKMbJqHHbgia3CVNibpQvalDLg4A/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

注：  

第 2 步中的**逗号**指的是英文半角逗号，我们这里的分隔符是中文全角逗号，需要在其他里面手动输入（如果是不认识的分隔符，可以复制粘贴到此处）；

第 3 步中更改学号一列的**数据格式**为文本，否则学号 001 会被表格当成数字处理为 1.

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMCByyyk4HEFpicVcAjiaVyX6hz32FtsfSDkoGMjbezrOysmHrDLo7NnFUQ/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

2. 按**固定宽度**进行分列：提取编码中的一部分

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMCBwMGmcKn6LqXdsujnVyufu3C2VPc1kCLcY8JAkkDgiaUgBMP1qmzjAA/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMCZwMpnGy0xbTuxxPdSkMDc6guY22XWGkj5ndQjTnrM624ZenpO6FPLg/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

注：每一步骤都有提示文字，看一下就能理解哦

## 用函数实现截取部分字符串（编码）

**`LEFT/RIGHT/MID`**（左边/右边/中间截取）

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMCK5w3G2T6icR2JCL2Go7mReiaFrA22n0Zew93dSNUQpNW4G9qx4WZt6sA/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

左边截取与之同理，中间截取：

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMCyGeibyytm9ibB5SzR450JvX2mcaz7NjsDmEsyf47UONrjL4ic2ZjreT4w/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

为什么要引入这几个函数？

应用：

### 从身份证中提取地区、生日、性别等信息

（已有编码前六位对应地区工作表）

姓名及身份证号除地区码外均为虚构

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMCzxNYDqiaTvjpibibribaHvo20Yj64BpEcnRbsbhdLa0FZrtqIeItia80t6g/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

地区码工作表中的编码均为数值格式，而 LEFT 等函数查找的内容均为文本，所以要利用上节所学把文本转数字。  

## 求余函数 MOD

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMCuZfoZIia7Ie4c0nCmTKibic7PmItKMIxjXjTguNdJh9gmdzbYw0n1Rw8A/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

### 利用求余函数 MOD**判断奇偶**

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMCTzic1tFBrVsPyOc2hFViaAbUBRoLd2Sq0JkQwaJp1bpibEe99XBNdqibmQ/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

与 MID 函数一起使用，**提取身份证中的性别信息**

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMC6Knn0KRccodFMIBY6GpIF8rwFLunXBNIer7IiaYNf7Z4CyOA8OqUZKg/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

建议由内向外写公式哦，便于排错。

到**出生日期**一项，数字如何转换成日期格式呢？改变单元格格式直接改为日期可行吗？

前面我们说过电子表格的日期本质上数字，1 表示 1900/01/01，2 表示 1900/01/02……并不是数字表面上的对应关系，19760517 并不能表示 1976 年 5 月 17 日，且电子表格的时间是有上限的，为 9999/12/31（转成数值格式为 2958465）远小于我们当前的数字。

下一节我们会讲到日期类函数，但这里我们不使用它也能实现：

首先改变显示样式为日期

设置单元格格式 - 数字 - 自定义（使用占位符 0 来进行格式设置）

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMCca2OcgLf1CnreboYfTvp0iacOsbA7xGRibMLdISRf4tUGUJX18waLQ5Q/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

如何把它变为真正的日期？利用 text 函数，前面有用过，它能根据指定的数值格式将数字转换成文本；在此基础上再转成数值：

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMCNW5nX33jHQ0Kp5daclh9bXd3TrUesbM3UjNywzOhG52mBx6VyFl3icA/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

上面的例子都是处理一些文本格式比较整齐的数据，如果要**处理长度不一样的数据**该怎么办呢？

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMCuWXCFIeX2QZs8Tz0gG1Oa9LQVjBpwAAj0AFhBAeib7lHyBwjDjhNNpQ/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

发现数据共同点，是以“@”符号分隔开的两个信息

又需要引入新**函数 FIND**，用于返回一个字符串在另一个字符串中的起始位置

举例：找“啥”在“你猜猜我要找啥“的那个位置上

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMCacIDrOiahL90lZHcrms7icKpN8oFKhZBibOgI2EN3UStWlZBWTdMpnnLw/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

应用 FIND 函数找到“@”的位置减去 1 即用户名文本的长度；关于域名思想与之类似，不过要用到后面的一个函数，看完后回过头来自己思考一下哦。

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMCtGl7wdRwvxvWnM6VZE60TyRH43GOKe7WmXmndmKFZv0RvzPPh57yfQ/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

### **分离数值和单位**

（尽量从输入时回避此类问题，即将数值与单位分隔输入）

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMCRNcozmeOfQrQZgoaRVdVmRtT4CaXpxgKwUpCu09GX8YVd1Pw5ZE2jA/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

引入 LEN（计算字符长度）与 LENB（计算字节长度）****

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMCdqia70IGl9asxJ5S8ibzmvMic6d7ia2KByMhYT1UHhYpgk1f8t7ATZptWQ/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

因为一个汉字两个字节，一个普通字符一个字节，A2 中文本的字符长度为 4，字节长度为 5，多出来的 1 是由一个汉字单位造成的，每多增加一个汉字，字节长度增加 1，则可以用多出来的字节数代表汉字个数（单位的长度），由此：

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMCgVbc4rGmziaVvrCs7hU9Cb92ULE79f73Qv6fkic0GM67vNZUAO7XvzJw/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

接下来也可以轻易分离出数值

注意：数值要从文本转换

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMCe1aN3NHcyTITJNj0X1Y5wCIwA7ZE8eicLhOmJdvyrXATv8p0fpqzx4g/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

其他相关问题

身份证最后一位是什么含义呢？

公民身份号码是特征组合码，由十七位数字本体码和一位数字校验码组成。其排列顺序从左至右依次为：六位数字地址码，八位数字出生日期码，三位数字顺序码和一位数字**校验码**。

公民身份号码国家标准 GB11643-1999

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMClXu9rlXGvpib4ary0cibJzQxs4YntC3csMOjyjh4vA5bq9A4G2AoeyTQ/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

因为刚才的身份证号是随意编造的的所以最末一位校验码并不对。

借鉴这种思想，我们可以为 n 为数的产品编号也设置一位校验码 [前（n-1）除某个数取余结果]，这样在某一位书写错误时可以直接得到系统的反馈，大大降低出错可能。

假设有原来产品编码有 8 位，现在加一位校验码为前 8 位除以 9 的余数，降低输入错误可能。在数据验证中添加公式：

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMCdnHeEzotnmRq0fiaEQFdytxK1O2qBg7QEPIXhTTLiaibiaKwZdxGJVx2Cw/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrOia5fC58KQ12G5GCianP5nMC7uicFqhCibTHwaTCdD3YmmZzVTicVch2ufJVg7wqJmicfCia51gic4T0volg/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)