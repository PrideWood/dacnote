---
date created: 2024-03-03T09:33:20+08:00
date modified: 2024-03-03T23:25:38+08:00
---

## 文件的编码

编码是一种规则集合，记录了内容和二进制间进行相互转换的逻辑。
编码有许多中，我们最常用的是 UTF-8 编码

## 文件的读取

`open()` 打开函数

语法：`open(name, mode, encoding)`

- name：是要打开的目标文件名的字符串 (可以包含文件所在的具体路径)
- mode：设置打开文件的模式 (访问模式)：只读、写入、追加等。
- encoding: 编码格式（推荐使用 UTF-8）

示例代码

```python
f = open('python.txt', 'r', encoding=”UTF-8)
# encoding的顺序不是第三位，所以不能用位置参数，用关键字参数直接指定
```

注意：此时的 `f` 是 `open` 函数的文件对象，对象是 Python 中一种特殊的数据类型，拥有属性和方法，可以使用 `对象.属性` 或 `对象.方法` 对其进行访问

mode 常用的三种基础访问模式

| 模式  | 描述                                                                |
| --- | ----------------------------------------------------------------- |
| r   | 以只读方式打开文件。文件的指针将会放在文件的开头。这是默认模式。                                  |
| w   | 打开一个文件只用于写入。如果该文件已存在则打开文件，并从开头开始编辑，原有内容会被删除。  <br>如果该文件不存在，创建新文件。 |
| a   | 打开一个文件用于追加。如果该文件已存在，新的内容将会被写入到已有内容之后。  <br>如果该文件不存在，创建新文件进行写入。    |

### 操作汇总

| 操作                                | 功能                         |
| --------------------------------- | -------------------------- |
| 文件对象 = open(file, mode, encoding) | 打开文件获得文件对象                 |
| 文件对象.read(num)                    | 读取指定长度字节  <br>不指定 num 读取文件全部 |
| 文件对象.readline()                   | 读取一行                       |
| 文件对象.readlines()                  | 读取全部行，得到列表                 |
| for line in 文件对象                  | for 循环文件行，一次循环得到一行数据        |
| 文件对象.close()                      | 关闭文件对象                     |
| with open() as f                  | 通过 with open 语法打开文件，可以自动关闭   |

练习：单词计数，统计指定 .txt 文件中某个单词的出现次数

## 文件的写入

示例代码

```python
# 1. 打开文件
f = open('python.txt', 'w')

# 2.文件写入
f.write('hello world')

# 3. 内容刷新
f.flush()

```

注意：
- 直接调用 write，内容并未真正写入文件，而是会积攒在程序的内存中，称之为缓冲区
- 当调用 flush 的时候，内容会真正写入文件
- 这样做是避免频繁的操作硬盘，导致效率下降（攒一堆，一次性写磁盘）
- 文件如果不存在，使用”w”模式，会创建新文件；文件如果存在，使用”w”模式，会将原有内容清空
- close() 方法，带有 flush() 方法的功能

## 文件的追加

代码示例

```python
# 1. 打开文件，通过a模式打开即可
f = open('python.txt', 'a')

# 2.文件写入
f.write('hello world')

# 3. 内容刷新
f.flush()

```

注意：
- a 模式，文件不存在会创建文件
- a 模式，文件存在会在最后，追加写入文件
- 可以使用 `\n` 来写出换行符

## 综合案例：文件备份

