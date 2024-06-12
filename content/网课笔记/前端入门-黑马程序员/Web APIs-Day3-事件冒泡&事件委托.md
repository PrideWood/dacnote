---
date created: 2024-02-22T09:55:47+08:00
date modified: 2024-02-23T12:49:49+08:00
---
案例：
- [全选文本框](C:\Users\24742\Desktop\practice\WebAPIs\Day3-全选按钮案例.html)

> 进一步学习 事件进阶，实现更多交互的网页特效，结合事件流的特征优化事件执行的效率

- 掌握阻止事件冒泡的方法
- 理解事件委托的实现原理

## 事件流

事件流是对事件执行过程的描述，了解事件的执行过程有助于加深对事件的理解，提升开发实践中对事件运用的灵活度。

![](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/event.png)

如上图所示，任意事件被触发时总会经历两个阶段：捕获阶段（Capture Phase）和**冒泡阶段（Event Bubbling）**。

简言之，捕获阶段是【从父到子】的传导过程，冒泡阶段是【从子向父】的传导过程。

### 捕获和冒泡

了解了什么是事件流之后，我们来看事件流是如何影响事件执行的：

```html
<body>
  <h3>事件流</h3>
  <p>事件流是事件在执行时的底层机制，主要体现在父子盒子之间事件的执行上。</p>
  <div class="outer">
    <div class="inner">
      <div class="child"></div>
    </div>
  </div>
  <script>
    // 获取嵌套的3个节点
    const outer = document.querySelector('.outer');
    const inner = document.querySelector('.inner');
    const child = document.querySelector('.child');
		
    // html 元素添加事件
    document.documentElement.addEventListener('click', function () {
      console.log('html...')
    })
		
    // body 元素添加事件
    document.body.addEventListener('click', function () {
      console.log('body...')
    })

    // 外层的盒子添加事件
    outer.addEventListener('click', function () {
      console.log('outer...')
    })
    
    // 中间的盒子添加事件
    inner.addEventListener('click', function () {
      console.log('inner...')
    })
    
    // 内层的盒子添加事件
    child.addEventListener('click', function () {
      console.log('child...')
    })
  </script>
</body>
```

执行上述代码后发现，当单击事件触发时，其祖先元素的单击事件也【相继触发】，这是为什么呢？

结合事件流的特征，我们知道当某个元素的事件被触发时，事件总是会先经过其祖先才能到达当前元素，然后再由当前元素向祖先传递，事件在流动的过程中遇到相同的事件便会被触发。

再来关注一个细节就是事件相继触发的【执行顺序】，事件的执行顺序是可控制的，即可以在捕获阶段被执行，也可以在冒泡阶段被执行。

如果事件是在冒泡阶段执行的，我们称为冒泡模式，它会先执行子盒子事件再去执行父盒子事件，默认是冒泡模式。

如果事件是在捕获阶段执行的，我们称为捕获模式，它会先执行父盒子事件再去执行子盒子事件。

```html
<body>
  <h3>事件流</h3>
  <p>事件流是事件在执行时的底层机制，主要体现在父子盒子之间事件的执行上。</p>
  <div class="outer">
    <div class="inner"></div>
  </div>
  <script>
    // 获取嵌套的3个节点
    const outer = document.querySelector('.outer')
    const inner = document.querySelector('.inner')

    // 外层的盒子
    outer.addEventListener('click', function () {
      console.log('outer...')
    }, true) // true 表示在捕获阶段执行事件
    
    // 中间的盒子
    inner.addEventListener('click', function () {
      console.log('inner...')
    }, true)
  </script>
</body>
```

结论：

1. `addEventListener` 第 3 个参数决定了事件是在捕获阶段触发还是在冒泡阶段触发
2. `addEventListener` 第 3 个参数为 `true` 表示捕获阶段触发，`false` 表示冒泡阶段触发，默认值为 `false`
3. 事件流只会在父子元素具有相同事件类型时才会产生影响
4. 绝大部分场景都采用默认的冒泡模式（其中一个原因是早期 IE 不支持捕获）

### 阻止冒泡

阻止冒泡是指阻断事件的流动，保证事件只在当前元素被执行，而不再去影响到其对应的祖先元素。

语法

```js
事件对象.stopPropagation()
```

```html
<body>
  <h3>阻止冒泡</h3>
  <p>阻止冒泡是指阻断事件的流动，保证事件只在当前元素被执行，而不再去影响到其对应的祖先元素。</p>
  <div class="outer">
    <div class="inner">
      <div class="child"></div>
    </div>
  </div>
  <script>
    // 获取嵌套的3个节点
    const outer = document.querySelector('.outer')
    const inner = document.querySelector('.inner')
    const child = document.querySelector('.child')

    // 外层的盒子
    outer.addEventListener('click', function () {
      console.log('outer...')
    })

    // 中间的盒子
    inner.addEventListener('click', function (ev) {
      console.log('inner...')

      // 阻止事件冒泡
      ev.stopPropagation()
    })

    // 内层的盒子
    child.addEventListener('click', function (ev) {
      console.log('child...')

      // 借助事件对象，阻止事件向上冒泡
      ev.stopPropagation()
    })
  </script>
</body>
```

结论：事件对象中的 `ev.stopPropagation` 方法，专门用来阻止事件冒泡。

## 事件解绑

```html
<body>
  <button>点击</button>
  <script>
    const btn = document.querySelector('button')
    // btn.onclick = function () {
    //   alert('点击了')
    //   // L0 事件移除解绑
    //   btn.onclick = null
    // }
    function fn() { // 注意：匿名函数无法解绑
      alert('点击了')
    }
    btn.addEventListener('click', fn)
    // L2 事件移除解绑
    btn.removeEventListener('click', fn)
  </script>
</body>
```

>鼠标经过事件：
>
>mouseover 和 mouseout 会有冒泡效果
>
>**mouseenter 和 mouseleave** 没有冒泡效果 (推荐)

## 事件委托

事件委托是利用事件流的特征解决一些现实开发需求的知识技巧，主要的作用是提升程序效率。

大量的事件监听是比较耗费性能的，如下代码所示

```html
<script>
  // 假设页面中有 10000 个 button 元素
  const buttons = document.querySelectorAll('table button');

  for(let i = 0; i <= buttons.length; i++) {
    // 为 10000 个 button 元素添加了事件
    buttons.addEventListener('click', function () {
      // 省略具体执行逻辑...
    })
  }
</script>
```

利用事件流的特征，可以对上述的代码进行优化，事件的的冒泡模式总是会将事件流向其父元素的，如果父元素监听了相同的事件类型，那么父元素的事件就会被触发并执行，正是利用这一特征对上述代码进行优化，如下代码所示：

```html
<script>
  // 假设页面中有 10000 个 button 元素
  let buttons = document.querySelectorAll('table button');
  
  // 假设上述的 10000 个 buttom 元素共同的祖先元素是 table
  let parents = document.querySelector('table');
  parents.addEventListener('click', function () {
    console.log('点击任意子元素都会触发事件...');
  })
</script>
```

我们的最终目的是保证只有点击 button 子元素才去执行事件的回调函数，如何判断用户点击是哪一个子元素呢？

![](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/event.png)

事件对象中的属性 `target` 或 `srcElement` 属性表示真正触发事件的元素，它是一个元素类型的节点。

```html
<script>
  // 假设页面中有 10000 个 button 元素
  const buttons = document.querySelectorAll('table button')
  
  // 假设上述的 10000 个 buttom 元素共同的祖先元素是 table
  const parents = document.querySelector('table')
  parents.addEventListener('click', function (ev) {
    // console.log(ev.target);
    // 只有 button 元素才会真正去执行逻辑
    if(ev.target.tagName === 'BUTTON') {
      // 执行的逻辑
    }
  })
</script>
```

优化过的代码只对祖先元素添加事件监听，相比对 10000 个元素添加事件监听执行效率要高许多！！！

案例：[事件委托形式切换tab栏](C:\Users\24742\Desktop\practice\WebAPIs\Day3-事件委托tab栏切换.html)

补充：阻止默认行为：某些情况下阻止默认行为的发生，如阻止连接的跳转，表单域跳转

语法：

```js
e.preventDefault()
```

示例代码：

```html
<body>
  <form action="http://www.itcast.cn">
    <input type="submit" value="免费注册">
  </form>
  <a href="http://www.baidu.com">百度一下</a>
  <script>
    const form = document.querySelector('form')
    form.addEventListener('submit', function (e) {
      // 阻止默认行为  提交
      e.preventDefault()
    })

    const a = document.querySelector('a')
    a.addEventListener('click', function (e) {
      e.preventDefault()
    })
  </script>
</body>
```

## 其他事件

### 页面加载事件

加载外部资源（如图片、外联 CSS 和 JavaScript 等）加载完毕时触发的事件

有些时候需要等页面资源全部处理完了做一些事情

**事件名：load**

监听页面所有资源加载完毕：

~~~javascript
window.addEventListener('load', function() {
    // xxxxx
})

// 了解
document.addEventListener('DOMContentLoaded', function(){
	// 执行的操作
})
~~~

### 元素滚动事件

滚动条在滚动的时候持续触发的事件

~~~javascript
window.addEventListener('scroll', function() {
    // xxxxx
})
~~~

scrollLeft 和 scrollTop （属性）
- 获取被卷去的大小
- 获取元素内容往左、往上滚出去看不到的距离
- 这两个值是**可读写**的
尽量在 scroll 事件里面获取被卷去的距离

案例：[页面滚动事件](C:\Users\24742\Desktop\practice\WebAPIs\Day3-页面滚动事件.html)

scrollTop 细节

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    body {
      height: 3000px;
    }
  </style>
</head>

<body>
  <script>
    document.documentElement.scrollTop = 800
    window.addEventListener('scroll', function () {
      // 必须写到里面
      const n = document.documentElement.scrollTop
      // 得到是什么数据   数字型 不带单位
      // console.log(n)
    })
  </script>
</body>

</html>
```

案例：[电梯导航](C:\Users\24742\Desktop\practice\WebAPIs\电梯导航素材\电梯导航.html)

### 页面尺寸事件

会在窗口尺寸改变的时候触发事件：

~~~javascript
window.addEventListener('resize', function() {
    // xxxxx
})

// 检测屏幕宽度
window.addEventListener('resize', function(){
	let w = document.documentElement.clientWidth
	console.log(w)
})
~~~

获取宽高：
- 获取元素的可见部分宽高（不包含边框，margin，滚动条等）
- clientWidth 和 clientHeight

![image.png|350](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240222201034.png)

学习到此阶段可以读懂 flexible.js 源码

## 元素尺寸与位置

### 获取宽高

- 获取元素的自身宽高、包含元素自身设置的宽高、padding、border
- offsetWidth 和 offsetHeight  
- 获取出来的是数值，方便计算
注意: 获取的是可视宽高，如果盒子是隐藏的，获取的结果是 0

### 获取位置

方法一
- 获取元素距离自己定位父级元素的左、上距离
- offsetLeft 和 offsetTop 是**只读**属性

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    div {
      position: relative;
      width: 200px;
      height: 200px;
      background-color: pink;
      margin: 100px;
    }

    p {
      width: 100px;
      height: 100px;
      background-color: purple;
      margin: 50px;
    }
  </style>
</head>

<body>
  <div>
    <p></p>
  </div>
  <script>
    const div = document.querySelector('div')
    const p = document.querySelector('p')
    // console.log(div.offsetLeft)
    // 检测盒子的位置  最近一级带有定位的祖先元素
    console.log(p.offsetLeft)
  </script>
</body>

</html>
```

案例：
- [仿新浪固定头部案例](C:\Users\24742\Desktop\practice\WebAPIs\Day3-仿新浪固定头部.html)
- bilibili 移动端首页，选中 tab 下移动的线条效果代码段

![GIF 2024-2-23 12-39-22.gif|500](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/GIF%202024-2-23%2012-39-22.gif)

```js
<script>
    // 1. 事件委托的方法 获取父元素 tabs-list
    const list = document.querySelector('.tabs-list')
    const line = document.querySelector('.line')
    // 2. 注册点击事件
    list.addEventListener('click', function (e) {
      // 只有点击了A 才有触发效果
      if (e.target.tagName === 'A') {
        // console.log(11)
        // 当前元素是谁 ？  e.target
        // 得到当前点击元素的位置
        // console.log(e.target.offsetLeft)
        // line.style.transform = 'translateX(100px)'
        // 把我们点击的a链接盒子的位置  然后移动
        line.style.transform = `translateX(${e.target.offsetLeft}px)`
      }
    })

  </script>
```

方法二
- `element.getBoundingClientRect()` 返回元素的大小及其相对于视口的位置

### 小结

| **属性**                     | **作用**               | **说明**                                 |
|----------------------------|----------------------|----------------------------------------|
| scrollLeft 和 scrollTop       | 被卷去的头部和左侧            | 配合页面滚动来用，可读写                           |
| clientWidth 和 clientHeight | 获得元素宽度和高度            | 不包含 border、margin、滚动条，用于 js 获取元素大小，只读属性 |
| offsetWidth 和 offsetHeight   | 获得元素宽度和高度            | 包含 border、padding、滚动条等，只读               |
| offsetLeft 和 offsetTop       | 获取元素距离自己定位父级元素的左、上距离 | 获取元素位置的时候使用，只读属性                       |

## 综合案例

- [电梯导航](C:\Users\24742\Desktop\practice\WebAPIs\电梯导航素材\电梯导航.html)

需求：点击不同的模块，页面可以自动跳转不同的位置

模块分析：
1. 页面滚动到对应位置，导航显示，否则隐藏模块
2. 点击导航对应小模块，页面 会跳到对应大模块位置
3. 页面滚动到对应位置，电梯导航对应模块自动发生变化
