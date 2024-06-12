---
date created: 2024-02-01T14:34:15+08:00
date modified: 2024-02-02T10:45:49+08:00
---
学习目标

- 能够说出 3~5 个 HTML5 新增布局和表单标签
- 能够说出 CSS3 的新增特性有哪些

# HTML5 新特性

## 概述

HTML5 的新增特性主要是针对于以前的不足，增加了一些新的标签、新的表单和新的表单属性等。 

这些新特性都有兼容性问题，基本是 **IE9+ 以上版本的浏览器**才支持，如果不考虑兼容性问题，可以大量使用这些新特性。

## 语义化标签 （★★）

以前布局，我们基本用 div 来做。div 对于搜索引擎来说，是没有语义的

```html
<div class=“header”> </div>
<div class=“nav”> </div>
<div class=“content”> </div>
<div class=“footer”> </div>
```

发展到了 HTML5 后，新增了一些语义化标签，这样的话更加有利于浏览器的搜索引擎搜索，也方便了网站的 seo（Search Engine Optimization，搜索引擎优化），下面就是新增的一些语义化标签

- `<header>` 头部标签
- `<nav>` 导航标签
- `<article>` 内容标签
- `<section>` 定义文档某个区域
- `<aside>` 侧边栏标签
- `<footer>` 尾部标签

![语义化标签.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/%E8%AF%AD%E4%B9%89%E5%8C%96%E6%A0%87%E7%AD%BE.png)

## 多媒体标签

多媒体标签分为 音频 **audio** 和视频 **video** 两个标签 使用它们，我们可以很方便的在页面中嵌入音频和视频，而不再去使用落后的 flash 和其他浏览器插件了。

因为多媒体标签的 属性、方法、事件比较多，因此我们需要什么功能的时候，就需要去查找相关的文档进行学习使用。

### 视频标签 - video（★★★）

#### 基本使用

当前 `<video>` 元素支持三种视频格式： 尽量使用 **mp4 格式**

**使用语法：**

```html
 <video src="media/mi.mp4"></video>
```

![video支持格式.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/video%E6%94%AF%E6%8C%81%E6%A0%BC%E5%BC%8F.png)

#### 兼容写法

由于各个浏览器的支持情况不同，所以我们会有一种兼容性的写法，这种写法了解一下即可

```html
<video  controls="controls"  width="300">
    <source src="move.ogg" type="video/ogg" >
    <source src="move.mp4" type="video/mp4" >
    您的浏览器暂不支持 <video> 标签播放视频
</ video >
```

**上面这种写法，浏览器会匹配 video 标签中的 source，如果支持就播放，如果不支持往下匹配，直到没有匹配的格式，就提示文本**

#### video 常用属性

![video常用属性.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/video%E5%B8%B8%E7%94%A8%E5%B1%9E%E6%80%A7.png)

**属性很多，有一些属性需要大家重点掌握：**

- `autoplay` 自动播放
  - 注意： 在 google 浏览器上面，默认禁止了自动播放，如果想要自动播放的效果，需要设置 muted 属性
- `width` 宽度
- `height` 高度
- `loop` 循环播放
- `src` 播放源
- `muted` 静音播放

**示例代码：**

```html
<video src="media/mi.mp4" autoplay="autoplay" muted="muted"  loop="loop" poster="media/mi9.jpg"></video>
```

### 音频标签 - audio

#### 基本使用

当前 `<audio> ` 元素支持三种视频格式： 尽量使用 **mp3 格式**

**使用语法：**

```html
<audio src="media/music.mp3"></audio>
```

![audio支持格式.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/audio%E6%94%AF%E6%8C%81%E6%A0%BC%E5%BC%8F.png)

#### 兼容写法

由于各个浏览器的支持情况不同，所以我们会有一种兼容性的写法，这种写法了解一下即可

```html
< audio controls="controls"  >
    <source src="happy.mp3" type="audio/mpeg" >
    <source src="happy.ogg" type="audio/ogg" >
    您的浏览器暂不支持 <audio> 标签。
</ audio>
```

**上面这种写法，浏览器会匹配 audio 标签中的 source，如果支持就播放，如果不支持往下匹配，直到没有匹配的格式，就提示文本**

#### audio 常用属性

**示例代码：**

```html
<audio src="media/music.mp3" autoplay="autoplay" controls="controls"></audio>
```

### 小结

- 音频标签和视频标签使用方式基本一致
- 浏览器支持情况不同
- 谷歌浏览器把音频和视频自动播放禁止了
- 我们可以给视频标签添加 muted 属性来静音播放视频，音频不可以（可以通过 JavaScript 解决）
- 视频标签是重点，我们经常设置自动播放，不使用 controls 控件，循环和设置大小属性

#### 新增的表单元素 （★★）

在 H5 中，帮我们新增加了很多类型的表单，这样方便了程序员的开发

**课堂案例：在这个案例中，熟练了新增表单的用法**

![input案例.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/input%E6%A1%88%E4%BE%8B.png)

**案例代码：**

```html
<!-- 我们验证的时候必须添加form表单域 -->
<form action="">
    <ul>
        <li>邮箱: <input type="email" /></li>
        <li>网址: <input type="url" /></li>
        <li>日期: <input type="date" /></li>
        <li>时间: <input type="time" /></li>
        <li>数量: <input type="number" /></li>
        <li>手机号码: <input type="tel" /></li>
        <li>搜索: <input type="search" /></li>
        <li>颜色: <input type="color" /></li>
        <!-- 当我们点击提交按钮就可以验证表单了 -->
        <li> <input type="submit" value="提交"></li>
    </ul>
</form>
```

 **常见输入类型**

```
text password radio checkbox button file hidden submit reset image
```

**新的输入类型**

![新增input表单.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/%E6%96%B0%E5%A2%9Einput%E8%A1%A8%E5%8D%95.png)

类型很多，我们现阶段**重点记忆三个**： **`number`   `tel`   `search`**

#### 新增的表单属性

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240201172557.png)

示例代码：

```css
input:: placeholder{
	color: #333;
}
```

# CSS3 新特性

## CSS3 的现状

- 新增的 CSS3 特性有兼容性问题，ie9+ 才支持
- 移动端支持优于 PC 端 
- 不断改进中 
- 应用相对广泛
- 现阶段主要学习：新增选择器和盒子模型以及其他特性 

## CSS3 新增选择器 

CSS3 给我们新增了选择器，可以更加便捷，更加自由的选择目标元素。 

- 属性选择器
- 结构伪类选择器
- 伪元素选择器

### 属性选择器（★★）

属性选择器，按照字面意思，都是根据标签中的属性来选择元素

![](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/%E5%B1%9E%E6%80%A7%E9%80%89%E6%8B%A9%E5%99%A8.png)

**示例代码：**

```css
 /* 只选择 type =text 文本框的input 选取出来 */
input[type=text] {
    color: pink;
}
/* 选择首先是div 然后 具有class属性 并且属性值 必须是 icon开头的这些元素 */
div[class^=icon] {
    color: red;
}
/* 选择首先是section 然后 具有class属性 并且属性值 必须是 data结尾的这些元素 */
section[class$=data] {
    color: blue;
}
```

- 属性选择器，按照字面意思，都是根据标签中的属性来选择元素
- 属性选择器可以根据元素特定属性的来选择元素。 这样就可以不用借助于类或者 id 选择器
- 属性选择器也可以选择出来自定义的属性
- **注意：** 类选择器、属性选择器、伪类选择器，权重为 10。

### 结构伪类选择器

结构伪类选择器主要**根据文档结构**来选择元素， 常用于根据父级选择器里面的子元素

![](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/%E7%BB%93%E6%9E%84%E4%BC%AA%E7%B1%BB%E9%80%89%E6%8B%A9%E5%99%A8-01.png)

#### `E:first-child`

匹配父元素的第一个子元素 E

```html
 <style>
    ul li:first-child{
      background-color: red;
    }
  </style>

  <ul>
    <li>列表项一</li>
    <li>列表项二</li>
    <li>列表项三</li>
    <li>列表项四</li>
  </ul>
```

![](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/first-child.png)

**E:last-child**  则是选择到了最后一个 li 标签

#### `E:nth-child(n)`（★★★）

匹配到父元素的第 n 个元素

- 匹配到父元素的第 2 个子元素 `ul li:nth-child(2){}`
- 匹配到父元素的序号为奇数的子元素 `ul li:nth-child(odd){}`    **odd** 是**关键字**  奇数的意思（3 个字母 ）
- 匹配到父元素的序号为偶数的子元素 `ul li:nth-child(even){}`   **even**（4 个字母 ）
- **匹配到父元素的前 3 个子元素**  `ul li:nth-child(-n+3){}` 如果 n 是公式，则从 0 开始计算，但是第 0 个元素或者超出了元素的个数会被忽略   

  选择器中的  **n** 是怎么变化的呢？

  因为 n 是从 0 ，1，2，3.. 一直递增，  所以 -n+3 就变成了   

  - n=0 时 -0+3=3
  - n=1 时 -1+3=2
  - n=2 时 -2+3=1
  - n=3 时 -3+3=0 
  - ...

**一些常用的公式： 公式不是死的，在这里列举出来让大家能够找寻到这个模式，能够理解代码，这样才能写出满足自己功能需求的代码**

![nth-child公式.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/nth-child%E5%85%AC%E5%BC%8F.png)

**常用的结构伪类选择器是：** `nth-child(n) {...}`

#### `E:nth-child` 与 `E:nth-of-type` 的区别

这里只讲明  **E:nth-child(n)**  和 **E:nth-of-type(n)**  的区别  剩下的 **E:first-of-type**     **E:last-of-type**  **E:nth-last-of-type(n)**   同理做推导即可

```html
<style>
    ul li:nth-child(2){
      /* 字体变成红色 */
        color: red;
    }

    ul li:nth-of-type(2){
      /* 背景变成绿色 */
      background-color: green;
    }
  </style>


  <ul>
    <li>列表项一</li>
    <p>乱来的p标签</p>
    <li>列表项二</li>
    <li>列表项三</li>
    <li>列表项四</li>
  </ul>
```

![nth-child与nth-of-type区别.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/nth-child%E4%B8%8Enth-of-type%E5%8C%BA%E5%88%AB.png)

也就是说：

- `E:nth-child(n)` 匹配父元素的第 n 个子元素 E，也就是说，nth-child 对父元素里面所有孩子排序选择（序号是固定的）  先找到第 n 个孩子，然后看看是否和 E 匹配
- `E:nth-of-type(n)` 匹配同类型中的第 n 个同级兄弟元素 E，也就是说，对父元素里面指定子元素进行排序选择。 先去匹配 E ，然后再根据 E 找第 n 个孩子

#### 小结

- 结构伪类选择器一般用于选择父级里面的第几个孩子
- nth-child 对父元素里面所有孩子排序选择（序号是固定的）  先找到第 n 个孩子，然后看看是否和 E 匹配
- nth-of-type 对父元素里面指定子元素进行排序选择。 先去匹配 E ，然后再根据 E 找第 n 个孩子
- 关于 nth-child（n） 我们要知道 n 是从 0 开始计算的，要记住常用的公式
- 如果是无序列表，我们肯定用 nth-child 更多
- 类选择器、属性选择器、伪类选择器，权重为 10

### 伪元素选择器（★★★）

伪元素选择器可以帮助我们利用 CSS 创建新标签元素，而不需要 HTML 标签，从而简化 HTML 结构

![伪元素.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/%E4%BC%AA%E5%85%83%E7%B4%A0.png)

**示例 demo**

```html
<style>
    div {
        width: 200px;
        height: 200px;
        background-color: pink;
    }
    /* div::before 权重是2 */
    div::before {
        /* 这个content是必须要写的 */
        content: '我';
    }
    div::after {
        content: '小猪佩奇';
    }
</style>
<body>
    <div>
        是
    </div>
</body>
```

注意：

- before 和 after 创建一个元素，但是属于行内元素
- 新创建的这个元素在文档树中是找不到的，所以我们称为伪元素
- 语法：  `element::before {}`
- before 和 after **必须有 content 属性** 
- before 在父元素内容的前面创建元素，after 在父元素内容的后面插入元素
  伪元素选择器和标签选择器一样，权重为 1

#### 应用场景一： 字体图标

[案例-伪元素字体图标](C:\Users\24742\Desktop\practice\HTML\CSS-Day8-伪元素字体图标.html)

在实际工作中，字体图标基本上都是用伪元素来实现的，好处在于我们不需要在结构中额外去定义字体图标的标签，通过 content 属性来设置字体图标的 编码

**步骤：**

- 结构中定义 div 盒子
- 在 style 中先申明字体  @font-face
- 在 style 中定义 after 伪元素 div::after{...}
- 在 after 伪元素中 设置 content 属性，属性的值就是字体编码
- 在 after 伪元素中 设置 font-family 的属性
- 利用定位的方式，让伪元素定位到相应的位置；记住定位口诀：子绝父相

#### 应用场景二： 仿土豆效果

把之前的代码进行了改善

**步骤：**

- 找到之前写过的仿土豆的结构和样式，拷贝到自己的页面中
- 删除之前的 mask 遮罩
- 在 style 中，给大的 div 盒子（类名叫 tudou 的），设置 before 伪元素
- 这个伪元素充当的是遮罩的角色，所以我们不用设置内容，但是需要设置 content 属性，属性的值为空字符串
- 给这个遮罩设置宽高，背景颜色，默认是隐藏的
- 当鼠标移入到 div 盒子时候，让遮罩显示，利用 hover 来实现

代码段示例：

```css
.tudou::before {
      content: '';
      /* 隐藏遮罩层 */
      display: none;
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, .4) url(images/arr.png) no-repeat center;
    }
    
/* 当我们鼠标经过了 土豆这个盒子，就让里面before遮罩层显示出来，注意中间不能有空格*/
    .tudou:hover::before {
      /* 而是显示元素 */
      display: block;
    }
```

#### 应用场景三： 清除浮动

回忆一下清除浮动的方式：

- 额外标签法也称为隔墙法，是 W3C 推荐的做法。
- 父级添加 overflow 属性
- 父级添加 after 伪元素
- 父级添加双伪元素

**额外标签法**也称为隔墙法，是 W3C 推荐的做法

![额外标签法.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/%E9%A2%9D%E5%A4%96%E6%A0%87%E7%AD%BE%E6%B3%95.png)

**注意：** 要求这个新的空标签必须是块级元素

后面两种伪元素清除浮动算是第一种额外标签法的一个**升级**和**优化**

![单伪元素.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/%E5%8D%95%E4%BC%AA%E5%85%83%E7%B4%A0.png)

![双伪元素.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/%E5%8F%8C%E4%BC%AA%E5%85%83%E7%B4%A0.png)

## 盒子模型（★★★）

CSS3 中可以通过 box-sizing 来指定盒模型，有 2 个值：即可指定为 content-box、border-box，这样我们计算盒子大小的方式就发生了改变

可以分成两种情况：

- `box-sizing: content-box` 盒子大小为 width + padding + border  （以前默认的）
- `box-sizing: border-box` 盒子大小为 width

如果盒子模型我们改为了 `box-sizing: border-box`  ， 那 padding 和 border 就不会撑大盒子了（前提 padding 和 border 不会超过 width 宽度），可以写在样式开头 `*{}` 里

## 其他特性（★）

### 图标变模糊 -- CSS3 滤镜 filter

filter CSS 属性将模糊或颜色偏移等图形效果应用于元素

**语法：**

```css
 filter: 函数();
```

例如：

```css
 filter: blur(5px); 
```

blur 模糊处理  数值越大越模糊

![](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/filter.png)

### 计算盒子宽度 -- calc 函数

calc() 此 CSS 函数让你在声明 CSS 属性值时执行一些计算

语法：

```css
width: calc(100% - 80px);
```

括号里面可以使用 `+` `-` `*`  `/` 来进行计算

## CSS3 过渡（★★★）

过渡（transition) 是 CSS3 中具有颠覆性的特征之一，我们可以在不使用 Flash 动画或 JavaScript 的情况下，当元素从一种样式变换为另一种样式时为元素添加效果。

**过渡动画：** 是从一个状态 渐渐的过渡到另外一个状态

可以让我们页面更好看，更动感十足，虽然 低版本浏览器不支持（ie9 以下版本） 但是不会影响页面布局。

我们现在经常和 :hover 一起 搭配使用。

语法：

```css
transition: 要过渡的属性  花费时间  运动曲线  何时开始;
```

- 属性 ： 想要变化的 css 属性， 宽度高度 背景颜色 内外边距都可以 。如果想要所有的属性都变化过渡， 写一个 all 就可以
- 花费时间： 单位是 秒（必须写单位） 比如 0.5s 
- 运动曲线： 默认是 ease （可以省略）
- 何时开始：单位是 秒（必须写单位）可以设置延迟触发时间  默认是 0s  （可以省略）
- **后面两个属性可以省略**
- **记住过渡的使用口诀： 谁做过渡给谁加**

![运动曲线.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/%E8%BF%90%E5%8A%A8%E6%9B%B2%E7%BA%BF.png)

#### 过渡练习

![](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/%E8%BF%9B%E5%BA%A6%E6%9D%A1.png)

步骤：

- 创建两个 div 的盒子，属于的嵌套关系，外层类名叫 bar，里层类名叫 bar_in
- 给外层的 bar 这个盒子设置边框，宽高，圆角边框
- 给里层的 bar_in 设置 初试的宽度，背景颜色，过渡效果
- 给外层的 bar 添加 hover 事件，当触发了 hover 事件 让里层的 bar_in 来进行宽度的变化

[案例-进度条效果](C:\Users\24742\Desktop\practice\HTML\CSS-Day8-过渡进度条.html)

# 广义 H5 说法 - 了解

### 狭隘 H5

![广义H5.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/%E5%B9%BF%E4%B9%89H5.png)

### 广义 H5

- 广义的 HTML5 是 HTML5 本身 + CSS3 + JavaScript 。
- 这个集合有时称为 HTML5 和朋友，通常缩写为 HTML5 。
- 虽然 HTML5 的一些特性仍然不被某些浏览器支持，但是它是一种发展趋势。