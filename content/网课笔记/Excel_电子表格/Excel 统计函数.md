---
date created: 2024-03-01T14:49:52+08:00
date modified: 2024-03-01T14:54:42+08:00
---
**Tips：**

- 养成更好的操作习惯，手动键盘输入公式（**英文输入法**模式下）
- 记不清楚函数的全拼，准确输入前几个字母，用**方向键 +Tab 键**在所给提示选项中选择
- 数据引用**支持跨表引用**

## 基础统计函数

^7f1cd5

`sum`, `average`, `max`, `min`, `max`, `count`（只数数字，不数文本）, `counta`（数非空单元格个数）

**批量填充公式**：先选中区域（如果是非连续的空白单元格可以使用定位功能定位空值单元格）- 写公式 -**Ctrl+Enter**

**问题**：（合并单元格的处理）在取消单元格合并后，单元格中的内容默认只填充首行单元格，现在要使得每一个空白单元格重复原单元格中的内容，该如何操作？

方法一：使用填充柄多次拖拉

方法二：以下图中的组别为例，如果组别非常多拖拉会很费时，我们可以：

选中表格内组别一栏所有的空单元格 - 批量填充公式（使得每一个单元格的值等于其正上方紧邻的单元格的值）

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrPmvQicp6dicXTMhlIHGQQrSlm9DsoXy11hicyebtmAzmrMT8XGlPIMYa2TPGHNRPzwuC7UuhPWMYcUg/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

注意：此时的表格中后填充的内容为公式，如果表格排序方式发生改变，由公式确定的单元格的值可能发生改变，为了防止改变，可对该列内容进行**复制 - 粘贴为值**操作。

**问题**：缴费基数问题：关于社保基数的详细信息可自行百度，此处对其缴费方式简单解释为，月薪达不到下限，需要按下限缴费，月薪超过上限按上限缴费，月薪在上下限之间则月薪即为缴费基数。假设某地区社保缴费基数下限为 2600，上限为 20000，则下表显示的是各个个人的缴费基数。

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrPmvQicp6dicXTMhlIHGQQrSlUY6srnDJqXLzZyl3VueMatIYfpVdhonAhf3lEOnZtCD4zwcsZL4PeQ/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

如何利用公式自动计算缴费基数呢？

解决方法：利用 `min` 和 `max` 函数，对它们进行**嵌套使用**

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrPmvQicp6dicXTMhlIHGQQrSlJoIdYuNoAbwkr4lSvrzlnQB0uRYKWdIbJLzuBE2np80HV8S1J5iaSNQ/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

## 条件统计函数

### `countif(range,criteria)`

**用来判定符合某条件的数据有几个**

**活用**：用 countif 进行多表**信息核对**（判断一组数据中有无数据满足一定的标准）

例：已知全班同学花名册，课代表提交上来一组已交同学名单，如何利用该函数判断哪些同学没交作业？

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrPmvQicp6dicXTMhlIHGQQrSlw7iaBlMckGf6dwNNnREgvicYGyg0gI7DD8TKhaqmxndudZU8c3lwLZGg/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

能看出来图中的 0 和 1 的含义吗？

注意：在进行选择数据范围时，如果**选择固定区域，需要绝对引用；如果选择一整列的范围则不需要考虑此问题。**

### `sumif(range,criteria,sum_range)`

**在指定区域内对满足某个条件的的某些信息的某项进行求和**

**活用**：用 `sumif` 进行**信息查询**

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrPmvQicp6dicXTMhlIHGQQrSlsIN8EdsRGWK7o1BvCEibAXaJw8OpYQ6vBHxJYtG9KZjJXklPw9B5ib3A/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

注意：如果有重名的情况就不能使用该方法了哦，可以改为根据学号查成绩。不能利用该函数查找非数字的数据。

`sumif` 的 sum_range 可以为单元格（一个**非典型用法**）

例：下表为一段时间内某人消费流水账，要对各个消费项目进行统计

如果是一般的流水账表（每一行对应一条信息），我们可以进行排序 - 分类汇总或直接使用数据透视表，但如果是下表的样式该如何处理？

![图片](https://mmbiz.qpic.cn/mmbiz_png/mhpgqe0LyrPmvQicp6dicXTMhlIHGQQrSlyw7mEu4JnKR1JzcaEcPR3AvsRA8gu2h1VicKWz4sCXEAUgkbFQ4KCwg/640?wx_fmt=png&tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrPmvQicp6dicXTMhlIHGQQrSlKQjoCCsM0icuQXo9ogjOoS6Q3ncKQS7pQ5bIiaOJ2hdicqMIX4r3gnSFw/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

注意：在这里我们引用数据范围和求和数据范围都要绝对引用。

方便起见，我们仍以此为例，再来看公式的另外两种允许的写法：

如果我们只需要总计吃饭一项的消费额，可以直接更改公式里的 criteria 为 " 吃饭”（**英文双引号**括起来的条件）

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrPmvQicp6dicXTMhlIHGQQrSlrIyuVAIl8tTz8uUjibQ6wpDaKSV6bLSbOrCrJHguMobR8Mzicic80epCQ/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

如果我们只需要总计消费额大于 100 的项目，可以更改公式为

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrPmvQicp6dicXTMhlIHGQQrSlc74XgBtabmfRNiaWib0TzEYIYAibOURDqEBqtJ8EG8YVucpmtEWlNwDBw/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

注意：因为此表格中只有消费额一项为数值信息，所以我们选定全表的范围也就是消费额的范围，因此需要删去 sum_range 项（如果 range 和 sum_range 为同一个，也可删去 sum-range），如果保留会计算出错（我们已经说过以单元格为 sum_range 范围是一个非典型用法）。

上一节我们提到：WPS 中拒绝录入重复值是数据验证（WPS 中称作数据有效性）中的功能。因为涉及到公式我们并作未进一步解释，现在我们一起用公式实现这个功能吧：

数据 - 数据验证 - 自定义 - 在公式一栏输入公式（此处我们以 C 列为例）

![图片](https://mmbiz.qpic.cn/mmbiz_png/lPXVB5QpAkTNxON5QUKfGKp7RBsibCVjxZo2w1L56PjyhVG9pbmsChZUlFljicYP5D4icMXCXJAkY5lYcyhscfDrg/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

公式的含义即在 C 列中，不允许出现两个值相同的单元格，其中选中整 C 列是否绝对引用无所谓，输入公式的单元格（即选定区域中第一个被选单元格，如下图绿框中无阴影填充的单元格）不能进行绝对引用，但如果选中有限的区域必须进行绝对引用。

![图片](https://mmbiz.qpic.cn/mmbiz_png/2E8PibShL6F6cH46N60VRZGVl1Q3jMYzaG8cFv9wQLqavCpnoYlWusAsyJw3LiamcPABPOTFw5pDGgkSw4w6O5jg/640?tp=wxpic&wxfrom=5&wx_lazy=1&wx_co=1)

注意 sumif, countif 的**使用限制**，对于**长度超过 15 的数字**可能无法区分：如果数字前 15 位相同则被认为是同一数字，出现如图的问题：

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrPmvQicp6dicXTMhlIHGQQrSl7j6LhdyFV1HIt0Y99sibZT3HLhT7oT1nPmkiajGLNCtiaz5ribaibSE86uA/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

如何解决此类问题呢？

还记得之前有一节可以用 `王*` 代表所有王姓同学吗？这个 `*` 中可包含的字符长度是无限制的，我们只需要把这个 `*` 加入公式即可；

但直接加也是不行的，此处引入一个**运算符 `&`**（连字符，把两个数据相连），其效果如下图：

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrPmvQicp6dicXTMhlIHGQQrSlp1daUNNFPFib6uPnh9ZwicL9QiclaR8ibV2KILGRoKX488HlD26MsHDtbw/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

还有一点要注意，**`*` 在运算中表示乘号，为了防止他被当做乘号，还需要加上英文双引号**

看看结果吧：

![图片](https://mmbiz.qpic.cn/mmbiz_gif/mhpgqe0LyrPmvQicp6dicXTMhlIHGQQrSlcibjAUYsXAIZ1QTuxwJVbb2o1vsbxibxrudxyNCzRjd6h1ibjlvj8gJGQ/640?wx_fmt=gif&tp=wxpic&wxfrom=5&wx_lazy=1)

类似的多条件统计函数：`sumifs`, `countifs`，只是条件增多其余用法和上述所讲相同。

为什么不讲 `averageif` 函数呢？因为我们可以通过上面两个相除即可得到 `averageif` 的结果~

Excel 表格中的公式 300~400 个左右，而其中 30~40 个即可解决商务场景中 95% 的问题，所以我们也只跟着王老师学习最重要的那些公式，本节课已经学习了超过 10 个啦。期待下次更新哦~