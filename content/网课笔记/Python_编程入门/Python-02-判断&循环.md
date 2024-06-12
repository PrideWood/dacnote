---
date created: 2024-02-23T16:36:50+08:00
date modified: 2024-02-24T14:14:17+08:00
---

# 判断语句

## 布尔类型和比较运算符

比较运算符

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240223164238.png)

## if 语句的基本格式

```python
if 判断条件:
    条件成立时，要做的事情。
```

举例：

```python
# 定义变量
age = 30

# 进行判断
if age >= 18:
	print("我已经成年了")

```

- 判断语句的结果，必须是布尔类型 True 或 False，True 会执行 if 内的代码语句，False 则不会执行
- 归属于 if 判断的代码语句块，需在前方填充 4 个**空格缩进**。Python 通过缩进判断代码块的归属关系。

## if else 语句

举例：

```python
print('欢迎光临')  
age = int(input('请输入您的年龄：'))  
if age >= 18:  
    print('您老了，请买票')  
else:  
    print('你还嫩，可免费')  
  
print('再次欢迎')

```

## if elif else 语句

举例

```python
# 可以在条件判断中，直接写input语句，节省代码量
if int(input('请输入您的年龄：')) >= 18:  
    print('请买票')  
elif int(input('您的会员等级：')) < 3:  
    print('请买票')  
else:  
    print('可免费')  

print('再次欢迎')

```

判断是互斥且有顺序的
- 满足 1（如图编号）将不会理会 2 和 3
- 满足 2，将不会理会 3
- 1、2、3 均不满足，进入 else
- else 也可以省略不写，效果等同 3 个独立的 if 判断

## 判断语句的嵌套

举例

```python
print('欢迎来到动物园')  
if int(input("你的身高")) > 120:  
    print('你好高，要买票')  
    print('不过如果你vip级别高，可以免费')  
  
    if int(input('你的vip级别：')) > 3:  
        print('尊贵的vip你好，可以免费')  
    else:  
        print('不好意思哈，要补票10块')  
else:  
    print('看在你这么矮的份儿上，可以免费')
```

## 实战案例

定义一个数字（1~10，随机产生），通过 3 次判断来猜出来数字

# 循环语句

## while 循环的基础语法

举例：

```python
i = 0  
while i < 100:  
    print("我喜欢你")  
    i += 1
```

案例：求 1-100 的和 参考代码

```python
sum = 0  
i = 1  
while i <= 100:  
    sum += i  
    i += 1  
print(f'1~100的和为 {sum}')
```

### 案例：猜数字游戏

设置一个范围 1-100 的随机整数变量，通过 while 循环，配合 input 语句，判断输入的数字是否等于随机数
- 无限次机会，直到猜中为止
- 每一次猜不中，会提示大了或小了
- 猜完数字后，提示猜了几次

参考代码：

```python
# 获取规定范围内的随机数  
import random  
num = random.randint(1,100)  
# print(num)  
  
# 定义一个记录猜测次数的变量  
count = 0  
  
# 通过一个布尔类型的变量 flag ,做循环是否继续的标记  
flag = True  
while flag:  
    guess_num = int(input('请输入你猜测的数字：'))  
    count += 1  
    print(f'你已经猜了 {count} 次了')  
    if guess_num == num:  
        print('猜中了')  
        # 设置为False就是终止循环的条件  
        flag = False  
    else:  
        if guess_num > num:  
            print('你猜大了')  
        else:  
            print('你猜小了')
```

### while 循环的嵌套应用

简单嵌套：背 100 天单词，每天背 10 个

```python
i = 1  
while i <= 100:  
    print(f'今天是背单词的第{i}天')  
    j = 1  
    while j <= 10:  
        print(f'今天已经背了{j}个单词')  
        j += 1  
    i +=  1  
print(f'恭喜你已经坚持了{i - 1}天，背完了所有单词')
```

### 案例：打印九九乘法表

补充知识

- print 输出不换行

在 print 语句中，输出默认会换行，而在本案例中，需要不换行，此时加上 `end=''` 即可输出不换行了，该方法是使用的方法传参功能，见后续内容。

- 制表符 `\t`

在字符串中，有一个特殊符号：`\t`，效果等同于在键盘上按下：tab 键。
它可以让我们的多行字符串进行对齐 [^1]。

![image.png|300](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240224122959.png)

注意：该方法可能因字符串长度出现问题 [^2]

提示：
- 2 层循环，外层控制行，内层控制列
- 外层循环和内存循环的累加数字变量，用以辅助输出乘法表的数值

九九乘法表示例代码

```python
# 外层循环控制行的循环  
i = 1  
while i <= 9:  
    # 内层循环控制列的循环  
    j = 1  
    while j <= i:  
        print(f'{j} * {i} = {j * i}\t', end='')  
        j += 1  
    i += 1  
    print()
```

一定要**注意缩进**

## for 循环的基础语法

与 while 循环的区别
- while 循环的循环条件是自定义的，自行控制循环条件
- for 循环是一种”轮询”机制，是对一批内容进行”逐个处理”

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240224125403.png)

### 基础语法

```python
for 临时变量 in 待处理数据集: 
        循环满足条件时执行的代码
```

举例：

```python
# 定义字符串name  
name = '我爱学习'  
# for循环处理字符串  
for x in name:   
       print(x)
```

输出结果

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240224125944.png)

可见，for 循环是将字符串的内容：依次取出，因此 for 循环也被称之为：**遍历循环**

同 while 循环不同，for 循环是无法定义循环条件的。所以，理论上讲，Python 的 for 循环无法构建无限循环（被处理的数据集不可能无限大）

练习案例：计算字符串中某个字母的数量

提示：
1. 计数可以在循环外定义一个整数类型变量用来做累加计数
2. 判断是否为要找的字母，可以通过 if 语句结合比较运算符来完成

示例代码

```python
# 统计字符串中有多少个字母 e  
name = 'Home is not where you live but where they understand you.'  
count = 0  
for x in name:  
    if x =='e':  
        count += 1  
  
print(f'这句话中有字母“e” {count} 个')
```

### range 语句

上面 for 语句语法中的：待处理数据集，严格来说，称之为：**可迭代类型**
可迭代类型指，其内容可以一个个依次取出的一种类型，包括：字符串、列表、元组 等，目前只学习字符串类型，其余类型后续会学到。

通过 range 语句，我们可以获得一个简单的数字序列（可迭代类型的一种）。

#### 语法 1：`range(num)`

获取一个从 0 开始，到 num 结束的数字序列（不含 num 本身）。如 `range(5)` 取得的数据是：\[0, 1, 2, 3, 4]

#### 语法 2：`range(num1, num2)`

`
获得一个从 num1 开始，到 num2 结束的数字序列（不含 num2 本身）
如，range(5, 10) 取得的数据是：\[5, 6, 7, 8, 9]

#### 语法 3：`range(num1, num2, step)`

`
获得一个从 num1 开始，到 num2 结束的数字序列（不含 num2 本身），数字之间的步长，以 step 为准（step 默认为 1）
如，range(5, 10, 2) 取得的数据是：\[5, 7, 9]

#### for 循环遍历 range 序列

代码举例

```python
# for循环处理字符串
for i in range(5): 
       print(i)
```

range 的用途很多，多数用在 for 循环场景

练习案例：数有几个偶数

提示：
1. 序列可以使用：range(1, num) 得到
2. 偶数通过 if 来判断，判断数字余 2 是否为 0 即可

参考代码

```python
num = int(input('请输入要从 1 统计到数字几：'))  
  
count = 0  
  
for x in range(1, num):  
    if x % 2 == 0:  
        count += 1  
  
print(f'从 1 到 {num} 有 {count} 个偶数')
```

### 变量作用域

如果在 for 循环外部访问临时变量：实际上是可以访问到的，但在编程规范上，是不允许、不建议这么做的
解决方案：如需访问临时变量，可以预先在循环外定义它

### for 循环的嵌套应用

代码示例

```python
# 用for循环完成背100天单词每天背10个的案例  
i = 1  
for i in range(1, 101):  
    print(f'今天是背单词的第{i}天')  
    for j in range(1, 11):  
        print(f'今天已经背了{j}个单词')  
print(f'恭喜你已经坚持了{i}天，背完了所有单词')
```

for 和 while 两类循环语句是可以相互嵌套的

练习案例：for 循环打印九九乘法表

提示：
- 2 层循环，外层控制行，内层控制列
- 可使用 range 语句来得到数字序列进行 for 循环
- 内层 for 循环的 range 最大范围，取决于当前外层循环的数字

示例代码

```python
# 外层循环控制行的循环  
i = 1  
for i in range(1, 10):  
    # 内层循环控制列的循环  
    j = 1  
    for j in range(1, i + 1):  
        print(f'{j} * {i} = {j * i}\t', end='')  
    # 外层循环通过print输出一个回车  
    print()
```

## 循环中断 : break 和 continue

无论是 while 循环或是 for 循环，都是重复性的执行特定操作。在这个重复的过程中，会出现一些其它情况让我们不得不：
暂时跳过某次循环，直接进行下一次提前退出循环，不在继续。对于这种场景，Python 提供 continue 和 break 关键字，用以对循环进行临时跳过和直接结束。

continue
- continue 关键字用于：中断本次循环，直接进入下一次循环
- continue 可以用于： for 循环和 while 循环，效果一致
- continue 关键字只可以控制：它所在的循环**临时中断**

break
- break 关键字用于：直接结束所在循环
- break 可以用于： for 循环和 while 循环，效果一致
- break 关键字同样只可以控制：它所在的循环**永久中断**

## 综合案例：发绩效工资

发绩效工资：某公司，账户余额有 1W 元，给 20 名员工发绩效工资。
员工编号从 1 到 20，从编号 1 开始，依次领取工资，每人可领取 1000 元
领工资时，财务判断员工的绩效分（1-10）（随机生成），如果低于 5，不发工资，换下一位
如果工资发完了，结束发工资。

提示：
continue 用于跳过员工，break 直接结束发工资
if 判断余额，不要忘记发完工资后，余额减少 1000

参考代码

```python
money = 10000  
for i in range(1, 21):  
    import random  
    score = random.randint(1, 10)  
    if score < 5:  
        print(f'员工{i}号，绩效分{score},低于5，不发绩效工资，下一位')  
        continue  
    else:  
        money -= 1000  
        print(f'向员工{i}号发绩效工资 1000 元，公司账户还剩{money}元')  
        if money == 0:  
            print('公司没钱了，发不了了，向剩下的倒霉员工说声抱歉')  
            break
```

[^1]: Python 中制表符 `\t` 的使用 https://blog.csdn.net/weixin_45772041/article/details/108861310
[^2]: Python 制表符 `\t` 无法对齐问题 https://blog.csdn.net/qq_41931443/article/details/120190885
