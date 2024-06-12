## 异常

程序运行的过程中出现了错误

### 捕获异常

捕获异常的作用在于：提前假设某处会出现异常，做好提前准备，当真的出现异常的时候，可以有后续手段。

基本语法

```python
# 捕获常规异常
try:
    可能发生错误的代码
except:
    如果出现异常执行的代码

# 捕获指定异常：如果尝试执行的代码的异常类型和要捕获的异常类型不一致，则无法捕获异常。 一般try下方只放一行尝试执行的代码。
try:
    print(name)
except NameError as e:
    print('name变量名称未定义错误')

# 捕获多个异常：当捕获多个异常时，可以把要捕获的异常类型的名字，放到except 后，并使用元组的方式进行书写
try:
    print(1/0)
except (NameError, ZeroDivisionError):
    print('ZeroDivision错误...')

# 捕获异常并输出异常信息
try:
    print(num)
except (NameError, ZeroDivisionError) as e:
    print(e)

# 捕获所有异常
try:
    print(name)
except Exception as e:
    print(e)

# else表示的是如果没有异常要执行的代码
try:
    print(1)
except Exception as e:
    print(e)
else:
    print('我是else，是没有异常的时候执行的代码')

# finally表示的是无论是否异常都要执行的代码，例如关闭文件
try:
    f = open('test.txt', 'r')
except Exception as e:
    f = open('test.txt', 'w')
else:
    print('没有异常，真开心')
finally:
    f.close()

```

异常具有传递性， 当所有函数都没有捕获异常的时候，程序就会报错

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240305210054.png)

利用该特点, 当我们想要保证程序不会因为异常崩溃的时候，就可以在main函数中设置异常捕获, 由于无论在整个程序哪里发生异常, 最终都会传递到main函数中, 这样就可以确保所有的异常都会被捕获

## Python模块

Python 模块(Module)，是一个 Python 文件，以 .py 结尾.  模块能定义函数，类和变量，模块里也能包含可执行的代码.

导入模块语法：`[from 模块名] import [模块 | 类 | 变量 | 函数 | *] [as 别名]`

常用的组合形式如：
- import 模块名
- from 模块名 import 类、变量、方法等
- from 模块名 import *
- import 模块名 as 别名
- from 模块名 import 功能名 as 别名

注意：
- from可以省略，直接import即可
- as别名可以省略
- 通过`.`来确定层级关系
- 模块的导入一般写在代码文件的开头位置

## Python包
## 安装第三方Python包