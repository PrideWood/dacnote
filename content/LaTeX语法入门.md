---
tags:
date created: 2024-01-28T22:23:20+08:00
date modified: 2024-03-08T11:38:14+08:00
---
Cited from: https://zhuanlan.zhihu.com/p/110756681

LaTeX，始于公式，忠于优雅...

## 数学模式

在 LaTeX 数学模式中，公式有两种形式——**行内公式**和**行间公式**。前者公式嵌入在行内，适用于简单短小的公式；后者居中独占一行，适用于比较长或重要的公式。公式中的空格均会被忽略，可以使用命令 `\quad` 或 `\qquad` 实现  
在行间公式中，命令 `\tag{n}` 可以进行手动编号

### 行内公式

```latex
$f(x) = a+b$
```

显示效果： $f(x) = a+b$

### 行间公式

```latex
$$f(x) = a+b$$
```

显示效果：$$f(x) = a+b$$

### 手动编号

```latex
$$ f(x) = a - b \tag{1.1} $$
```

显示效果：$$ f(x) = a - b \tag{1.1} $$

## 数学结构

### 简单运算

拉丁字母、阿拉伯数字和 `+ - * / =` 运算符均可以直接输入获得，命令 `\cdot` 表示乘法的圆点，命令 `\neq` 表示不等号，命令 `\equiv` 表示恒等于，命令 `\bmod` 表示取模

```latex
$$ x+2-3*4/6=4/y + x\cdot y $$
```

显示效果：$$ x+2-3*4/6=4/y + x\cdot y $$

```latex
$$ 0 \neq 1 \quad x \equiv x \quad 1 = 9 \bmod 2 $$
```

显示效果：$$ 0 \neq 1 \quad x \equiv x \quad 1 = 9 \bmod 2 $$

### 上下标

语法 `_` 表示下标、`^` 表示上标，但上下标内容不止一个字符时，需用大括号括起来。单引号 `'` 表示求导

```latex
$$ a_{ij}^{2} + b^3_{2}=x^{t} + y' + x''_{12} $$
```

显示效果：$$ a_{ij}^{2} + b^3_{2}=x^{t} + y' + x''_{12} $$

### 根号、分式

命令：`\sqrt` 表示平方根，`\sqrt[n]` 表示 n 次方根，`\frac` 表示分式

```latex
$$\sqrt{x} + \sqrt{x^{2}+\sqrt{y}} = \sqrt[3]{k_{i}} - \frac{x}{m}$$
```

显示效果：$$\sqrt{x} + \sqrt{x^{2}+\sqrt{y}} = \sqrt[3]{k_{i}} - \frac{x}{m}$$

### 上下水平线

命令：`\overline`, `\underline` 分别在表达式上、下方画出水平线

```latex
$$\overline{x+y} \qquad \underline{a+b}$$
```

显示效果：$$\overline{x+y} \qquad \underline{a+b}$$

命令：`\overbrace`, `\underbrace` 分别在表达式上、下方给出一个水平的大括号

```latex
$$\overbrace{1+2+\cdots+n}^{n个} \qquad \underbrace{a+b+\cdots+z}_{26}$$
```

显示效果：$$\overbrace{1+2+\cdots+n}^{n个} \qquad \underbrace{a+b+\cdots+z}_{26}$$

### 向量

命令：`\vec` 表示向量，`\overrightarrow` 表示箭头向右的向量，`\overleftarrow` 表示箭头向左的向量

```latex
$$\vec{a} + \overrightarrow{AB} + \overleftarrow{DE}$$
```

显示效果：$$\vec{a} + \overrightarrow{AB} + \overleftarrow{DE}$$

### 积分、极限、求和、乘积

命令：`\int` 表示积分，`\lim` 表示极限， `\sum` 表示求和，`\prod` 表示乘积，`^`、`_` 表示上、下限

```latex
$$ \lim_{x \to \infty} x^2_{22} - \int_{1}^{5}x\mathrm{d}x + \sum_{n=1}^{20} n^{2} = \prod_{j=1}^{3} y_{j} + \lim_{x \to -2} \frac{x-2}{x} $$
```

显示效果：$$ \lim_{x \to \infty} x^2_{22} - \int_{1}^{5}x\mathrm{d}x + \sum_{n=1}^{20} n^{2} = \prod_{j=1}^{3} y_{j} + \lim_{x \to -2} \frac{x-2}{x} $$

### 三圆点

命令：`\ldots` 点位于基线上，`\cdots` 点设置为居中，`\vdots` 使其垂直，`\ddots` 对角线排列

```latex
$$ x_{1},x_{2},\ldots,x_{5} \quad x_{1} + x_{2} + \cdots + x_{n} $$
```

显示效果：$$ x_{1},x_{2},\ldots,x_{5} \quad x_{1} + x_{2} + \cdots + x_{n} $$

### 重音符号

常用命令如下：

```latex
$\hat{x}$
$\bar{x}$
$\tilde{x}$
```

显示效果：
$\hat{x}$
$\bar{x}$
$\tilde{x}$

### 矩阵

其采用矩阵环境实现矩阵排列，常用的矩阵环境有 matrix、bmatrix、vmatrix、pmatrix，其区别为在于外面的括号不同：

![](https://pic1.zhimg.com/v2-684e48900e810dff360c23b4ffe99680_b.jpg)

下列代码中，`&` 用于分隔列，`\\` 用于分隔行

```latex
$$\begin{bmatrix} 1 & 2 & \cdots \\ 67 & 95 & \cdots \\ \vdots & \vdots & \ddots \\ \end{bmatrix}$$
```

显示效果：$$\begin{bmatrix} 1 & 2 & \cdots \\ 67 & 95 & \cdots \\ \vdots & \vdots & \ddots \\ \end{bmatrix}$$

### 希腊字母

希腊字母无法直接通过美式键盘输入获得。在 LaTeX 中通过反斜杠 `\` 加上其字母读音实现，将读音首字母大写即可输入其大写形式，详见下表

```latex
$$ \alpha^{2} + \beta = \Theta $$
```

显示效果：$$ \alpha^{2} + \beta = \Theta $$

![](https://pic1.zhimg.com/v2-da3e717cf670582fbfbdddee33073524_b.jpg)

### 多行公式

### 公式组合

通过 cases 环境实现公式的组合，`&` 分隔公式和条件，还可以通过 `\limits` 来让 `x→0` 位于 `lim` 的正下方而非默认在 `lim` 符号的右下方显示

```latex
$$D(x) = \begin{cases} \lim\limits_{x \to 0} \frac{a^x}{b+c}, & x<3 \\ \pi, & x=3 \\ \int_a^{3b}x_{ij}+e^2 \mathrm{d}x,& x>3 \\ \end{cases}$$
```

显示效果：$$D(x) = \begin{cases} \lim\limits_{x \to 0} \frac{a^x}{b+c}, & x<3 \\ \pi, & x=3 \\ \int_a^{3b}x_{ij}+e^2 \mathrm{d}x,& x>3 \\ \end{cases}$$

### 拆分单个公式

通过 split 环境实现公式拆分

```latex
$$\begin{split} \cos 2x &= \cos^2x - \sin^2x \\ &=2\cos^2x-1 \end{split}$$
```

显示效果：$$\begin{split} \cos 2x &= \cos^2x - \sin^2x \\ &=2\cos^2x-1 \end{split}$$

## 更多补充

### 小于等于和大于等于

```latex
\leq  %为小于等于
%示例
$ 1 \leq 2 $   %注意间隔，多加总没问题
%同理
\geq  %为大于等于
```

$$1 \leq 2$$

### 四种不同的 latex 的省略号

1. `\cdots` 是横向的居中的省略号
2. `\vdots` 是竖向的省略号
3. `\ddots` 是对角线方向的省略号
4. `\ldots`  是跟文本底线对齐的省略号
$$ \cdots \vdots  \ddots  \ldots $$

## 集合相关符号

https://blog.51cto.com/mouday/3049157

## 各种箭头符号

http://www.hijtr.com/latex-arrows/

## 在 Markdown 中使用 LaTeX

https://www.cnblogs.com/nowgood/p/Latexstart.html

updating...

