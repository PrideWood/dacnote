---
date created: 2024-02-21T13:14:10+08:00
date modified: 2024-02-21T20:49:24+08:00
---


> 学会通过为 DOM 注册事件来实现可交互的网页特效。

- 能够判断函数运行的环境并确字 this 所指代的对象
- 理解事件的作用，知道应用事件的 3 个步骤

## 事件

事件是编程语言中的术语，它是用来描述程序的行为或状态的，**一旦行为或状态发生改变，便立即调用一个函数。**

例如：用户使用【鼠标点击】网页中的一个按钮、用户使用【鼠标拖拽】网页中的一张图片

###  事件监听

结合 DOM 使用事件时，需要为 DOM 对象添加事件监听，等待事件发生（触发）时，便立即调用一个函数。

语法：

```javascript
元素对象.addEventListener('事件类型', 要执行的函数)
```

三要素：
1. 事件源： 那个 dom 元素被事件触发了，要获取 dom 元素
2. 事件类型： 用什么方式触发，比如鼠标单击 click、鼠标经过 mouseover 等
3. 事件调用的函数： 要做什么事

注意：
1. 事件类型要加引号
2. 函数是点击之后再去执行，每次点击都会执行一次

`addEventListener` 是 DOM 对象专门用来添加事件监听的方法，它的两个参数分别为【事件类型】和【事件回调】。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>事件监听</title>
</head>
<body>
  <h3>事件监听</h3>
  <p id="text">为 DOM 元素添加事件监听，等待事件发生，便立即执行一个函数。</p>
  <button id="btn">点击改变文字颜色</button>
  <script>
    // 1. 获取 button 对应的 DOM 对象
    const btn = document.querySelector('#btn')

    // 2. 添加事件监听
    btn.addEventListener('click', function () {
      console.log('等待事件被触发...')
      // 改变 p 标签的文字颜色
      let text = document.getElementById('text')
      text.style.color = 'red'
    })

    // 3. 只要用户点击了按钮，事件便触发了！！！
  </script>
</body>
</html>
```

完成事件监听分成 3 个步骤：

1. 获取 DOM 元素
2. 通过 `addEventListener` 方法为 DOM 节点添加事件监听
3. 等待事件触发，如用户点击了某个按钮时便会触发 `click` 事件类型
4. 事件触发后，相对应的回调函数会被执行

大白话描述：所谓的事件无非就是找个机会（事件触发）调用一个函数（回调函数）。

案例：
- [点击关闭](C:\Users\24742\Desktop\practice\WebAPIs\Day2-点击关闭.html)
- [随机点名](C:\Users\24742\Desktop\practice\WebAPIs\Day2-随机点名.html)

事件监听版本
发展史：
- DOM L0 ：是 DOM 的发展的第一个版本； L：level
- DOM L1：DOM 级别 1 于 1998 年 10 月 1 日成为 W3C 推荐标准
- DOM L2：使用 addEventListener 注册事件
- DOM L3： DOM3 级事件模块在 DOM2 级事件的基础上重新定义了这些事件，也添加了一些新事件类型
注意：
- DOM L0 `事件源.on事件 = function() { }`
- DOM L2 `事件源.addEventListener(事件， 事件处理函数)`
- 区别：on 方式会被覆盖，addEventListener 方式可绑定多次，拥有事件更多特性，推荐使用

### 事件类型

`click` 译成中文是【点击】的意思，它的含义是监听（等着）用户鼠标的单击操作，除了【单击】还有【双击】`dblclick`

```html
<script>
  // 双击事件类型
  btn.addEventListener('dblclick', function () {
    console.log('等待事件被触发...');
    // 改变 p 标签的文字颜色
    const text = document.querySelector('.text')
    text.style.color = 'red'
  })

  // 只要用户双击击了按钮，事件便触发了！！！
</script>
```

结论：【事件类型】决定了事件被触发的方式，如 `click` 代表鼠标单击，`dblclick` 代表鼠标双击。

### 事件处理程序

`addEventListener` 的第 2 个参数是函数，这个函数会在事件被触发时立即被调用，在这个函数中可以编写任意逻辑的代码，如改变 DOM 文本颜色、文本内容等。

```html
<script>
  // 双击事件类型
  btn.addEventListener('dblclick', function () {
    console.log('等待事件被触发...')
    
    const text = document.querySelector('.text')
    // 改变 p 标签的文字颜色
    text.style.color = 'red'
    // 改变 p 标签的文本内容
    text.style.fontSize = '20px'
  })
</script>
```

结论：【事件处理程序】决定了事件触发后应该执行的逻辑。

## 事件类型

将众多的事件类型分类可分为：鼠标事件、键盘事件、表单事件、焦点事件等，我们逐一展开学习。

### 鼠标事件

鼠标事件是指跟鼠标操作相关的事件，如单击、双击、移动等。

1. `mouseenter` 监听鼠标是否移入 DOM 元素

```html
<body>
  <h3>鼠标事件</h3>
  <p>监听与鼠标相关的操作</p>
  <hr>
  <div class="box"></div>
  <script>
    // 需要事件监听的 DOM 元素
    const box = document.querySelector('.box');

    // 监听鼠标是移入当前 DOM 元素
    box.addEventListener('mouseenter', function () {
      // 修改文本内容
      this.innerText = '鼠标移入了...';
      // 修改光标的风格
      this.style.cursor = 'move';
    })
  </script>
</body>
```

2. `mouseleave` 监听鼠标是否移出 DOM 元素

```html
<body>
  <h3>鼠标事件</h3>
  <p>监听与鼠标相关的操作</p>
  <hr>
  <div class="box"></div>
  <script>
    // 需要事件监听的 DOM 元素
    const box = document.querySelector('.box');

    // 监听鼠标是移出当前 DOM 元素
    box.addEventListener('mouseleave', function () {
      // 修改文本内容
      this.innerText = '鼠标移出了...';
    })
  </script>
</body>
```

综合案例：[轮播图完整版](C:\Users\24742\Desktop\practice\WebAPIs\Day2-轮播图完整版.html)

###  键盘事件

keydown 键盘按下触发
keyup 键盘抬起触发

代码段示例：

```html
<body>
  <input type="text">
  <script>
    const input = document.querySelector('input')
    // 1. 键盘事件
    // input.addEventListener('keydown', function () {
    //   console.log('键盘按下了')
    // })
    // input.addEventListener('keyup', function () {
    //   console.log('键盘谈起了')
    // })
    // 2. 用户输入文本事件  input
    input.addEventListener('input', function () {
      console.log(input.value)
    })
  </script>
</body>
```

### 焦点事件

- focus 获得焦点
- blur 失去焦点

代码段示例：

```html
<body>
  <input type="text">
  <script>
    const input = document.querySelector('input')
    input.addEventListener('focus', function () {
      console.log('有焦点触发')
    })
    input.addEventListener('blur', function () {
      console.log('失去焦点触发')
    })
  </script>
</body>
```

案例：[小米搜索框](C:\Users\24742\Desktop\practice\WebAPIs\Day2-小米搜索框.html)

### 文本框输入事件

input  

补充：focus 伪类选择器

示例代码：

```css
input {
      width: 200px;
      transition: all .3s;
    }

    /* focus伪类选择器  获得焦点 */
    input:focus {
      width: 300px;
    }
```

案例：[显示评论长度](C:\Users\24742\Desktop\practice\WebAPIs\Day2-显示评论长度.html)

## 事件对象

任意事件类型被触发时与事件相关的信息会被以对象的形式记录下来，我们称这个对象为事件对象。

```html
<body>
  <h3>事件对象</h3>
  <p>任意事件类型被触发时与事件相关的信息会被以对象的形式记录下来，我们称这个对象为事件对象。</p>
  <hr>
  <div class="box"></div>
  <script>
    // 获取 .box 元素
    const box = document.querySelector('.box')

    // 添加事件监听
    box.addEventListener('click', function (e) {
      console.log('任意事件类型被触发后，相关信息会以对象形式被记录下来...');

      // 事件回调函数的第1个参数即所谓的事件对象
      console.log(e)
    })
  </script>
</body>
```

事件回调函数的【第 1 个参数】即所谓的事件对象，通常习惯性的将这个对数命名为 `event`、`ev` 、`e` 。

接下来简单看一下事件对象中包含了哪些有用的信息：

1. `ev.type` 当前事件的类型
2. `ev.clientX/Y` 光标相对浏览器窗口的位置
3. `ev.offsetX/Y` 光标相于当前 DOM 元素的位置
4. `key` 用户按下的键盘键的值，现在不提倡使用 keyCode

注：在事件回调函数内部通过 window.event 同样可以获取事件对象。

案例：[按下回车发布评论](C:\Users\24742\Desktop\practice\WebAPIs\Day2-按下回车发布评论.html)

## 环境对象

> 能够分析判断函数运行在不同环境中 this 所指代的对象。

环境对象指的是函数内部特殊的变量 `this` ，它代表着当前函数运行时所处的环境。

```html
<script>
  // 声明函数
  function sayHi() {
    // this 是一个变量
    console.log(this);
  }

  // 声明一个对象
  let user = {
    name: '张三',
    sayHi: sayHi // 此处把 sayHi 函数，赋值给 sayHi 属性
  }
  
  let person = {
    name: '李四',
    sayHi: sayHi
  }

  // 直接调用
  sayHi() // window
  window.sayHi() // window

  // 做为对象方法调用
  user.sayHi()// user
	person.sayHi()// person
</script>
```

结论：

1. `this` 本质上是一个变量，数据类型为对象
2. 函数的调用方式不同 `this` 变量的值也不同
3. **【谁调用 `this` 就是谁】** 是判断 `this` 值的粗略规则
4. 函数直接调用时实际上 `window.sayHi()` 所以 `this` 的值为 `window`

## 回调函数

如果将函数 A 做为参数传递给函数 B 时，我们称函数 A 为回调函数 (callback)。

```html
<script>
  // 声明 foo 函数
  function foo(arg) {
    console.log(arg);
  }

  // 普通的值做为参数
  foo(10);
  foo('hello world!');
  foo(['html', 'css', 'javascript']);

  function bar() {
    console.log('函数也能当参数...');
  }
  // 函数也可以做为参数！！！！
  foo(bar);
</script>
```

函数 `bar` 做参数传给了 `foo` 函数，`bar` 就是所谓的回调函数了！！！

我们回顾一下间歇函数 `setInterval` 

```html
<script>
	function fn() {
    console.log('我是回调函数...');
  }
  // 调用定时器
  setInterval(fn, 1000);
</script>
```

`fn` 函数做为参数传给了 `setInterval` ，这便是回调函数的实际应用了，结合刚刚学习的函数表达式上述代码还有另一种更常见写法。

```html
<script>
  // 调用定时器，匿名函数做为参数
  setInterval(function () {
    console.log('我是回调函数...');
  }, 1000);
</script>
```

结论：

1. 回调函数本质还是函数，只不过把它当成参数使用
2. 使用匿名函数做为回调函数比较常见

案例：[tab 栏切换](C:\Users\24742\Desktop\practice\WebAPIs\Day2-tab栏切换.html)