---
date created: 2024-03-01T15:20:08+08:00
date modified: 2024-03-01T15:23:36+08:00
---
**开头 Get 一个新的快捷键**  

- **Ctrl+ 分号**即可快速在单元格中输入当前日期（某些输入法的快捷键可能覆盖掉这一快捷键）

## 日期相关计算

**YEAR, MONTH, DAY, DATE**

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcFWAQ7IVUId3NHmlia9ib1HRYwARTO6NFzFrPDvBvibyZjl95s78eYqZ9Fg/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcF4HpbgfWiaAYvxyNibRDK3d0CPkAIHq0d3S0AFJv6cm4fYkAyA144uQeQ/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

### 例. 计算结束日期  

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcFgypdrJfq6aR4ZutQPq2VriaC9aq0HJYcJPHwrP8rfE8JKBkbH5bkaOQ/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

利用 DATE 函数不会计算出非法日期的优点，我们可以用它来计算任意一个月的最后一天是几号而不需要人为考虑闰年。

我们无法确定每月的最后一天是多少号，但我们可以确定每月的第一天是一号，一号的前一天为上个月的最后一天，可写公式：

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcFpcXwwibnDLFh2MWh8RcuiaTj3UMnokvQCibWW9NnAUCYoWfQS1mLWHj3A/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcFZBr1Ns9N9iaB1A0vRpRCGiae9QPvZsmO9yMrUkpTMzhCBkjpH3pgiaMJQ/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

我们还可以采用第二张图上的公式写法，当 day 为 0 时就表示上个月最后一天（联系日期的实质是数字）

得知最后一天的日期我们也就得到了该月一共有多少天，在外侧套上一个 DAY 函数即可

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcFBTp4EOslnvkdlkBKzic1jh1g03uTcmJZFK469v9icTVibO43hapRSnzhA/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

进一步更改单元格格式即可。

既然引出了日期函数 date，我们上节课遗留的问题也就可以解决了：

转换 20191107 为日期，利用 date 函数和截取部分字符函数来做：

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcFfalic3EyclReK7b8qiaBZxVtcH583Pau8Rn4ZJKSMxibPZN1Y7YrnlPZQ/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

### **计算日期间隔**，以工龄为例

方法一：（不精确）（离职日期 - 入职日期）/365：没有考虑闰年的情况

方法二：DATEDIF 函数

注意计算时长时加 1 的问题，如从 1 日到 3 日直接做减法是 2，而实际时长为 3 日。  

表示年月日的字母 y, m, d 记得加引号

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcFYKbzXa1icyvNxhQHK6ykrtnXicCU9FZ90IexktNsnZbgEVQaTUX9j6tw/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

两个字母连用表示的含义：

ym 计算不满一年（y）的月数

md 计算不满一月（m）的天数

yd 计算不满一年（y）的天数

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcF3a9XoeTWRdIaHYFSNqEAc6L0SrhnoUdiaKiaJDaAkMSN56aBKG3ib2yicA/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

根据上面例子我们可以计算时间间隔并使其显示为 x 年 x 月 x 天

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcFOLicB5vX1biaRKrOmHL87vX4T2Ljibiam3C6L6ic3LQWjfwcOiaVCGsWcD8w/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

### **工作日计算**

NETWORKDAYS 函数

`Networkdays(start_days,end_days,[holidays])`

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcFXdPRicCRawNnOS62QD8wHSEtLUlXUg1Owkw0HUK1hVFSaColYvfu7jA/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

可是除了周末外还有一些法定节假日，全世界各国都有所不同，且可能根据当年情况进行修改，此时仅仅依靠上面的方法无法准确计算：  

首先建立一个法定节假日列表（无表头），将除去周末的节假日日期都放在同一列内,将此列数据作为函数的第三参数：

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcFwA8a0cfBZMcJJYHFp8FJqDF47iaklpQZgwicvh5r79o8KxBeVWD3ibl3g/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

知道日期算间隔，那如何根据间隔和起始日期算结束日期呢？  

一个与上个函数类似的 WORKDAY 函数：

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcF4Kgqw8D7JjqAV7JAztoR0CPvQ4ZoNIRvYMC2Qa3mjItrSj5e0voJpA/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

和上个动图对比起来看，这个算法算出的结束日期实际是我们常说的结束日期后一天，所以给该式子末尾减去 1 就与上面的对应了。  

## **星期相关运算**

### WEEKDAY **求周几**

return_type 可填 1/2/3，1 则周日~六对应数字 1~7；2 则周一~周日对应数字 1~7；3 则周一到周日对应数字 0~6。

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcFbQHLZxpMSyHHlTJJY4y45dEa6fjHicKfhOfdeGeeSZdUP7vtfXmDe2A/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

### WEEKNUM **求第几周**  

return_type 可填 1/2，1 表示周日为一周第一天，2 表示周一为一周第一天，按需要选择不同的类型，可能得到不同结果。

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcFEafialzmKhpvsn1FGZx5icgKooTibWNcPWy8OaZY5PaTGvOc9jLQ2n1oQ/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

## 日期函数与**条件格式**  

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcFx0ramjXFy2lfyZiaYbkRNicvniaeWAPOAW9XsJISJDrjc1GwIVcnY2vKg/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

我们要对今天未来十五天的时间进行突出显示，结合条件格式与上述函数：

不采用手动输入当天日期，否则每过一天需要对公式进行修改，有没有什么函数能够调取当天时间呢？

当然有：**TODAY 函数获取当天日期**，即使没有参数也要记得加括号：

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcFYicvbp4V2RiaPu2F2CicYze83Obqrr3AguWic1WAj7Xk3icsCtuAtqogRKg/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcFqDmjmu0DzVPuU8CyUd1auicMCm49UP01Adu3icAQNzC4MibngvkjqNBRg/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

## 时间相关运算

我们在单元格格式一节说过，日期都是数字，时间也是，前者是整数，后者是小数。

与 YEAR, MONTH, DAY, DATE 相对应的计算时间的函数有 HOUR, MINUTE, SECOND, TIME

电子表格中 1=1 天=24 小时=24`*`60 分钟，那么 1 小时=1/24，1 分钟=1/(24`*`60)

那么计算间隔时间时不需要函数，只需要**搞清楚换算关系**即可：（计算结果个格式可能需要手动调整）

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcF2If3TcYIXGLO3xU9micDzxctxEgkJDXERqllhta23fmUjIl89Jl8sWA/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcFuBEW8ZyBPZ0RqOU6xuuO251RuZjRHtasheP6djibh1wtoULQZtmXbWA/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcFKQMfLXbkKz1fQ6QfmWo8PRkWHicUkuBYbkvuPnJBtiaia9RugvnQ8E3FA/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

## 数学函数

### 四舍五入 ROUND

只能将长的小数部分舍去，不能增加 0 来使位数更加精确；

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcF3eicD8cziaibX3R6uMibp7Qyn9U5NnaibFeVSF41JTd320UBBCpvtwiaxPng/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

### 向上进位 ROUNDUP

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcFmI49gBMj1u44xCzIfjicF7tdkuhSYcrgM4IvVic4VmmBOfVfyV1JxSiaQ/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

### 直接舍去 ROUNDDOWN

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcFaRm0NrnTZMNuokhuOKf7eGcB3fZJX83nPuUbzEu1DZoXFxpb8ryaxQ/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

第二参数均支持为 0 甚至负数

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcFE4oWyQY4XzzGXfzI6NVj6s4xEyrZUrTzibCYg1Oku7tibKO5HSOXGpyw/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

其中 ROUNDDOWN 函数第二参数为 0 时，可作为**取整函数**使用

而取整函数还有一个**INT**，看一下它们两个的区别：

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcFcG5omGoO2WlIZWgmCNusnNg00wUTXkhjdDKcU80wbKeSY8EwrNBObw/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

### 多种方法计算解决同一个问题

某公司的休假制度，超过半天可休半天，不足半天不能休假，举例，理论休假 7.8 天实际只能休假 7.5 天；理论休假 4.3 天，实际只能休假 4 天，用函数实现：

此时还需要知道如何取数据的小数部分：

1. 原数字 - 整数部分
2. 除以 1 取余数

方法一：

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcF56KJFHw9Xvwy23ibxKicKL7pibxclR4Iia7PIoWAmJLIticNqXHVOdibAWQw/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

方法二：

利用数字规律，小数部分大于等于 0.5 的数乘以 2 后整数部分会产生进位，由此：

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcFib3Sib4tWTjGB2sDlltGvx5tLfSHYoFjbcT2HR0BkuWYAIpjzmETA3Lw/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

方法三：（不推荐）

新函数 FLOOR：将参数向下舍入为最接近的指定基数的倍数。

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrMo7DvL6RBojp7DbJrVEvcFrib5PynicHiaiapAtMHibGjlwgaalDGZh56vWm9CB0lEdYJmdHdpQHh9URA/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

处理商务场景中的所有函数我们都学完了，希望大家都能活学活用哦