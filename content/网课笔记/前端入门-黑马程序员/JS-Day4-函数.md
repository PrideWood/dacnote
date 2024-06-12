---
date created: 2024-01-23T10:27:31+08:00
date modified: 2024-02-18T11:56:46+08:00
---

> 理解封装的意义，能够通过函数的声明实现逻辑的封装，知道对象数据类型的特征，结合数学对象实现简单计算功能。

- 理解函数的封装的特征
- 掌握函数声明的语法
- 理解什么是函数的返回值
- 知道并能使用常见的内置函数

## 函数

> 理解函数的封装特性，掌握函数的语法规则

### 声明和调用

函数可以把具有相同或相似逻辑的代码“包裹”起来，通过函数调用执行这些被“包裹”的代码逻辑，这么做的优势是有利于精简代码方便复用。

#### 声明（定义）

声明（定义）一个完整函数包括关键字、函数名、形式参数、函数体、返回值 5 个部分

![function.jpg](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/function.jpg)

#### 调用

声明（定义）的函数必须调用才会真正被执行，使用 `()` 调用函数。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>JavaScript 基础 - 声明和调用</title>
</head>
<body>
  <script>
    // 声明（定义）了最简单的函数，既没有形式参数，也没有返回值
    function sayHi() {
      console.log('嗨~')
    }
    // 函数调用，这些函数体内的代码逻辑会被执行
    // 函数名()
        
    sayHi()
    // 可以重复被调用，多少次都可以
    sayHi()
  </script>
</body>
</html>
```

> 注：函数名的命名规则与变量是一致的，并且尽量保证函数名的语义。

小案例： 小星星

~~~javascript
<script>
        // 函数声明
        function sayHi() {
            // document.write('hai~')
            document.write(`*<br>`)
            document.write(`**<br>`)
            document.write(`***<br>`)
            document.write(`****<br>`)
            document.write(`*****<br>`)
            document.write(`******<br>`)
            document.write(`*******<br>`)
            document.write(`********<br>`)
            document.write(`*********<br>`)
        }
        // 函数调用
        sayHi()
        sayHi()
        sayHi()
        sayHi()
        sayHi()
    </script>
~~~

###  参数

通过向函数传递参数，可以让函数更加灵活多变，参数可以理解成是一个变量。

声明（定义）一个功能为打招呼的函数

- 传入数据列表
- 声明这个函数需要传入几个数据
- 多个数据用逗号隔开

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>JavaScript 基础 - 函数参数</title>
</head>
<body>

  <script>
    // 声明（定义）一个功能为打招呼的函数
    // function sayHi() {
    //   console.log('嗨~')
    // }
    // 调用函数
    // sayHi()
	

    // 这个函数似乎没有什么价值，除非能够向不同的人打招呼
    // 这就需要借助参数来实现了
    function sayHi(name) {
      // 参数 name 可以被理解成是一个变量
      console.log(name)
      console.log('嗨~' + name)
    }

    // 调用 sayHi 函数，括号中多了 '小明'
    // 这时相当于为参数 name 赋值了
    sayHi('小明')// 结果为 小明

    // 再次调用 sayHi 函数，括号中多了 '小红'
    // 这时相当于为参数 name 赋值了
    sayHi('小红') // 结果为 小红
  </script>
</body>
</html>
```

总结：

1. 声明（定义）函数时的形参没有数量限制，当有多个形参时使用 `,` 分隔
2. 调用函数传递的实参要与形参的顺序一致

#### 形参和实参

形参：声明函数时写在函数名右边小括号里的叫形参（形式上的参数）

实参：调用函数时写在函数名右边小括号里的叫实参（实际上的参数）

形参可以理解为是在这个函数内声明的变量（比如 num1 = 10）实参可以理解为是给这个变量赋值

开发中尽量保持形参和实参个数一致

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>JavaScript 基础 - 函数参数</title>
</head>
<body>
  <script>
    // 声明（定义）一个计算任意两数字和的函数
    // 形参 x 和 y 分别表示任意两个数字，它们是两个变量
    function count(x, y) {
      console.log(x + y);
    }
    // 调用函数，传入两个具体的数字做为实参
    // 此时 10 赋值给了形参 x
    // 此时 5  赋值给了形参 y
    count(10, 5); // 结果为 15
  </script>
</body>
</html>
```

为了让程序更加严谨，可以给形参设置默认值，如 `x = 0`, `arr = []`；实参也可以是变量

案例：[数组求和](C:\Users\24742\Desktop\practice\js\JS-Day4-函数封装数组求和.html)

### 返回值

函数的本质是封装（包裹），函数体内的逻辑执行完毕后，函数外部如何获得函数内部的执行结果呢？要想获得函数内部逻辑的执行结果，需要通过 `return` 这个关键字，将内部执行结果传递到函数外部，这个被传递到外部的结果就是返回值。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>JavaScript 基础 - 函数返回值</title>
</head>
<body>

  <script>
    // 定义求和函数
    function count(a, b) {
      let s = a + b
      // s 即为 a + b 的结果
      // 通过 return 将 s 传递到外部
      return s
    }

    // 调用函数，如果一个函数有返回值
    // 那么可将这个返回值赋值给外部的任意变量
    let total = count(5, 12)
  </script>
</body>
</html>
```

总结：

1. 在函数体中使用 return 关键字能将内部的执行结果交给函数外部使用
2. 函数内部只能出现 1 次 return，并且 return 下一行代码不会再被执行，所以 return 后面的数据不要换行写
3. return 会立即结束当前函数
4. 函数可以没有 return，这种情况默认返回值为 undefined

案例：[求最大值函数](C:\Users\24742\Desktop\practice\js\JS-Day4-求最大值函数.html)

**函数细节**

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>

<body>
  <script>
    // function getSum(x, y) {
    //   return x + y
    //   // 返回值返回给了谁？ 函数的调用者  getSum(1, 2)
    //   // getSum(1, 2) = 3
    // }
    // // let result = getSum(1, 2) = 3
    // // let num = parseInt('12px')
    // let result = getSum(1, 2)
    // console.log(result)
    // 1. 函数名相同， 后面覆盖前面

    // function fn() {
    //   console.log(1)
    // }
    // function fn() {
    //   console.log(2)
    // }
    // fn()
    // 2. 参数不匹配

    function fn(a, b) {
      console.log(a + b)
    }
    // (1). 实参多余形参   剩余的实参不参与运算
    // fn(1, 2, 3)
    // (2). 实参少于形参   剩余的实参不参与运算
    fn(1)   // 1 + undefined  = NaN 
  </script>
</body>

</html>
```

### 作用域

通常来说，一段程序代码中所用到的名字并不总是有效和可用的，而**限定这个名字的可用性的代码范围**就是这个名字的作用域。

作用域的使用提高了程序逻辑的局部性，增强了程序的可靠性，减少了名字冲突。

#### 全局作用域

作用于所有代码执行的环境 (整个 script 标签内部) 或者一个独立的 js 文件

处于全局作用域内的变量，称为全局变量

#### 局部作用域

**作用于函数内的代码环境**，就是局部作用域。 因为跟函数有关系，所以也称为函数作用域。

处于局部作用域内的变量称为局部变量

>如果函数内部，变量没有声明，直接赋值，也当全局变量看，但是强烈不推荐
>
>但是有一种情况，函数内部的形参可以看做是局部变量。

### 匿名函数

函数可以分为具名函数和匿名函数

匿名函数：没有名字的函数，无法直接使用。

#### 函数表达式

将匿名函数赋值给一个变量，并且通过变量名称进行调用，我们将这个称为函数表达式

~~~javascript
// 声明
let fn = function() { 
   console.log('函数表达式')
}
// 调用
fn()
~~~

#### 立即执行函数

避免全局变量之间污染

~~~javascript
(function(){xxxx})();
(function(){xxxx}());
~~~

建议书写顺序，先写两个`()`，在第一个里写函数

>无需调用，立即执行，其实本质已经调用了
>
>多个立即执行函数之间用**分号隔开**

​在能够访问到的情况下 先局部 局部没有在找全局

### 综合案例

[封装计算时间函数](C:\Users\24742\Desktop\practice\js\JS-Day4-综合案例：封装计算时间函数.html)

### 逻辑中断

JS-Day2 运算符里的短路 

![[JS-Day2-运算符#^fa14cd]]

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>

<body>
  <script>
    function fn(x, y) {
      x = x || 0
      y = y || 0
      console.log(x + y)
    }
    fn(1, 2)
    // fn()

    // console.log(false && 22)
    // console.log(false && 3 + 5)
    // let age = 18
    // console.log(false && age++) // age++ 不执行  一假则假
    // console.log(age)

    // console.log(true || age++)
    // console.log(age)


    // console.log(11 && 22)  // 都是真，这返回最后一个真值
    // console.log(11 || 22)  //  输出第一个真值
  </script>
</body>

</html>
```

### 转换为布尔型

`''`、`0`、`undefined`、`null`、`false`、`NaN` 转换为布尔型后均为 false，其余为true.

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>

<body>
  <script>
    console.log(Boolean('pink'))
    console.log(Boolean(''))
    console.log(Boolean(0))
    console.log(Boolean(90))
    console.log(Boolean(-1))
    console.log(Boolean(undefined))
    console.log(Boolean(null))
    console.log(Boolean(NaN))

    console.log('--------------------------')
    let age
    if (age) {
      console.log(11)
    }
  </script>
</body>

</html>
```

注意隐式转换：

1. 有字符串的加法 “” + 1 ，结果是 “1”
2. 减法 - （像大多数数学运算一样）只能用于数字，它会使空字符串 "" 转换为 0
3. null 经过数字转换之后会变为 0
4. undefined 经过数字转换之后会变为 NaN