---
date created: 2024-03-01T14:57:59+08:00
date modified: 2024-03-01T15:01:42+08:00
---
**函数中的比较判断**

你得先知道：

1）**不等于**的输入：<>（小于大于）
2）单元格内输入的**第一个等号**只是一个公式提示符（不包含在运算公式内）
3）单元格自带判断功能，如输入 1>2,显示 FALSE，判断结果 FALSE 和 TRUE 都是数字，**FALSE 为 0，TRUE 为 1**

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrPy8XB8wk6fiaFWr35GBjibHLqZHNBkSn5ib2kfLsiaJHXpRSYaLniaHk01030YZNzNibcibicwicLoIBRdeTg/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

（后面的例题中输入的的公式较长，动图演示不够简洁，以静态图片呈现，除姓名一栏外对于某个问题不涉及的信息设置了隐藏，请注意公式中引用单元格的位置）

双条件判断：给女生加分例题

① 只给女生加 30

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrPy8XB8wk6fiaFWr35GBjibHLtIYcqkiaQQSmggPian6EydhFqs87xsQOCRIGRzbmsjtzbhfkHaU3MwGA/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

② 如果是给男生加 20 分女生加 30 分要如何实现呢？

（提示：相当于只给女生比男生多加 10 分）

很明显这个方法应用场景十分有限，如果是更多条件，我们就得使用下面的函数：

## If 函数

![图片](https://mmbiz.qpic.cn/mmbiz_png/sPS0zfO6RLejTmODVOdPibLTVkvKbN4zaTgknUq9Xiaf7MvViakH0u15rf5Jcwm84TdUuiaMvbLRb7Su0VZicnia3NgQ/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

`If(logical_test,[value_if_true],[value_if_false])`

便于记忆：`如果____,就____,否则_____`.

例如，要标记所有男生为 B（boy），女生为 G（girl）

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrPy8XB8wk6fiaFWr35GBjibHL3zcfAficDZkkaYjRA1RYMDk24Axg5dZZ2gcAvxrx7lQbONlnMxkAkkQ/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

上面的例子仍然是两个条件（男 or 女），如果遇到下面的情况我们就需要利用多层级**if 的嵌套**

例：标记出所有同学的专业代号，以三个为例：

![图片](https://mmbiz.qpic.cn/mmbiz_png/wJjNbQZj8eSngerdiaEpnCXWopOFtxKZDwTpcibjZialZgVe4UZaBRKppwZAclZKv0mOiarhyIq7dwJDS2Y7lr7xwg/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

同理，还可以用 if 函数进行数值区段的连续划分，只需要改变条件为各个取值区段

例如：成绩在 600 以上评为优秀，成绩在 400~600 之间评为良好，成绩低于 400 评为一般

![图片](https://mmbiz.qpic.cn/mmbiz_png/f56uLGmjZvBTPwVOUKva7yKVG7AK2hx9fCqEicFbGUmLv1oxia5ib8KEVrWsXRQy27NgJmc3BmyWBbibsCpjeV7GTA/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

**注意：**

不能连写不等式：电子表格中 `400<=___<=600` 不能表示值的取值范围为 400~600，而对于连续区段可以直接依次向后写，if 函数对数据只做一次判断，一旦数值满足前面的条件则按照前面的结果输出，不会运算完整个公式。

## and 和 or 函数

这两个函数的结果输出均为 TRUE 或 FALSE

### `and(logical1,[logical2],…)`

![图片](https://mmbiz.qpic.cn/mmbiz_png/4GVfI0ibcHxdHSNCw9InBxzmWyHfqbEXdyUU8aic1RzD50ibW5hJnUblNdRvJlmhFicEtbF3duqx4h0iaK2ib5Ot9LYg/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

And 函数与乘法运算的作用一样，都表示且（逻辑与）

例：给成绩大于 600 分的男生以“掌声”作为奖励（两个条件是且的关系），其他同学没有奖励，标记为“无”

![图片](https://mmbiz.qpic.cn/mmbiz_png/FfSTDNybfgGX3y96AiagmyJh8Z2pjMFnUV7yKaouBwTyS5nqGOtTst6NJ1icvk23qowH0qKhdZUZmPZARBTu7RJQ/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

还没结束，我们要的是奖励：此时我们在将这个 and 嵌套进 if 函数中即可

![图片](https://mmbiz.qpic.cn/mmbiz_png/xAF3JwdXI6icW40tYhgOL8wjENpt5IER4IEnoHWq6Xdyhc8MMDnfY5jplL1mtWAWuoloowtJrbuCxQQ8N5IEVgA/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

我们**用逻辑与运算符“*”替换 and 函数**也能得到同样的结果

![图片](https://mmbiz.qpic.cn/mmbiz_png/Jhy1zUWbgpekFdYVdH41m6256Tkc2sXKLicHF9SSZIibQBOe1hFsSNLODyDFhLe2MncgFkyGiaqCjpbgWWJ6ljZag/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

### `or(logical1,[logical2],…`

![图片](https://mmbiz.qpic.cn/mmbiz_png/NmvYyHhwEc9Iuq86sRURVrKQf2PXYL7Ta6wSc1U6pScNsJ6WX973d5rT13KVeicDnBakO0s3CoGd4aBw0dg8r3A/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

与乘法运算的作用相同，都表示或（逻辑或）

例：给成绩 600 分以上或成绩 400 分以下的同学奖励“鲜花”

关于 or 函数的公式可根据 and 函数的样式写出，这里直接使用逻辑或运算符“+”

![图片](https://mmbiz.qpic.cn/mmbiz_png/IMtgyDO4tHzZEKjHk8ibvgZ9qxNtPzsvNx3etSd690jA5DzA0CbnISNK2KMOLMC4lg6ibZuEn239SvzLNq9ssLrg/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

复杂的条件往往需要与、或逻辑同时使用，在写公式前要先理清思路，判断清楚逻辑关系

例：给 600 分以上的男生、550 分以上的女生奖励“掌声”

![图片](https://mmbiz.qpic.cn/mmbiz_png/FfSTDNybfgGX3y96AiagmyJh8Z2pjMFnU9icfdVeMLJFfUnHuHMqGoXz8QSoVJg7iafgSK03sgAeQp8oaTZVazxuA/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

还没完，如果男生女生的奖励方式也不同呢？

看下图：

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/9tuuuJ0uTOSQbxXemPCibkwBRCKj33CQlyTj2ELlZfkYSFK0Ky9diazSI4jrY3tC4BB8yzgX0g60ricPg9br0keiaw/640?wxfrom=5&wx_lazy=1&wx_co=1)

## Iferror

![图片](https://mmbiz.qpic.cn/mmbiz_png/v36V1Ct6kk2QLbmoZ0PiczqyCTPaoH5ibH7Zia35OjEGaHLfiaj1pjRSTAtRr8vJZWNy3ucGhyHuxxubBXqpJjja0A/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

以**除 0 错误**为例，分母为 0 则表格显示为

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrPy8XB8wk6fiaFWr35GBjibHL2tLjcictmRFxJialRDVqKNOyproLqCUk3AevxXVgrbraFhmjDiaYmvQvQ/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

![图片](https://mmbiz.qpic.cn/mmbiz_png/r6vLyibSvuhPwiccTJzOibsyBZskwceNOopMh0oU1Q6YqHd0bcibt9DUmD8hyPF5C8PoIWDvlUFQMCibmmCeyibfRicPw/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

如果条件非常多，我们要用很多级 if 嵌套吗？当然不用！Vlookup 轻松搞定，请期待下次更新~