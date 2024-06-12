---
date created: 2024-01-25T15:15:34+08:00
date modified: 2024-02-07T08:47:35+08:00
---

## CSS 简介

CSS 是层叠样式表 ( Cascading Style Sheets ) 的简称，也称级联样式表
构成：**选择器**以及一条或多条**声明**

```css
<head> 
	<style> 
		h4 { color: blue; font-size: 100px; } 
	</style> 
</head>
```

- 属性和属性值以“键值对”的形式出现；
- 属性和属性值之间用英文“:”分开
- 多个“键值对”之间用英文“;”进行区分

推荐的代码风格：
推荐展开格式；小写格式；冒号和分号后、选择器（标签）和大括号中间保留空格

## CSS 基础选择器

基础选择器又包括：标签选择器、类选择器、id 选择器和通配符选择器

### 标签选择器

```
标签选择器 { 属性：属性值 ... }
```

### 类选择器

样式点定义， 结构类（class）调用，一个或多个，开发最常用

```
.类名 { 属性1: 属性值1; ... }
```

用 class 属性来调用的方式

```css
<div class="类名"> 变红色 </div>
```

[命名规范](https://itmyhome.com/front/index.html)

**多类名选择器**：一个标签有多个名字，各个类名使用空格隔开

```css
<div class="red font20">亚瑟</div> 
```

### id 选择器

样式 `#` 定义，结构 id 调用，只能调用一次，别人勿使用

```html
#id名 { 属性1: 属性值1; ... }
```

id 选择器和类选择器的区别： 
id 选择器一般用于页面**唯一性的元素**上，经常和 JavaScript 搭配使用。

### 通配符选择器

```
* { 属性1: 属性值1; ... }
```

通配符选择器不需要调用， 自动就给**所有的**元素使用样式
特殊情况才使用，后面讲解使用场景
以下是清除所有的元素标签的内外边距，后期讲

```css
* { 
	margin: 0; 
	padding: 0; 
}
```

Mini Review
![基础选择器总结.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/%E5%9F%BA%E7%A1%80%E9%80%89%E6%8B%A9%E5%99%A8%E6%80%BB%E7%BB%93.png)

## CSS 字体属性

写法：

```css
p { 
	font-family:'Microsoft Yahei';
	font-size: 20px;
	font-weight: bold;
	font-style: normal;
	}
```

实践中字体一般设置在 body 标签中:

```
body { 
	font-family:'Microsoft Yahei';
}
```

字体粗细 font-weight 属性值
![字体粗细.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/%E5%AD%97%E4%BD%93%E7%B2%97%E7%BB%86.png)

字体风格 font-style 属性值
![文字倾斜.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/%E6%96%87%E5%AD%97%E5%80%BE%E6%96%9C.png)

**字体的综合写法**
字体属性可以把以上文字样式综合来写, 这样可以更节约代码:

```
body { font: font-style font-weight font-size/line-height font-family;}
```

使用 font 属性时，必须按上面语法格式中的**顺序**书写，不能更换顺序，并且各个属性间以空格隔开 不需要设置的属性可以省略（取默认值），但**必须保留 font-size 和 font-family** 属性，否则 font 属性将不起作用

Mini Review
![字体总结.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/%E5%AD%97%E4%BD%93%E6%80%BB%E7%BB%93.png)

## CSS 文本属性

写法：

```css
div { 
	color: red; 
	text-align: center;
	text-decoration：underline；
	text-indent：20px；
	/* text-indent：2em；*/
	/* em 是一个相对单位，就是当前元素（font-size) 1 个文字的大小, 如果当前元素没有设置大小，则会按照父元素的 1 个文字大小。*/
	line-height: 26px;
}
```

文本颜色属性值
![颜色值.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/%E9%A2%9C%E8%89%B2%E5%80%BC.png)
开发中最常用的是十六进制

文本对齐属性值
![对齐文本.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/%E5%AF%B9%E9%BD%90%E6%96%87%E6%9C%AC.png)

修饰文本属性值
![修饰文本.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/%E4%BF%AE%E9%A5%B0%E6%96%87%E6%9C%AC.png)

文本缩进

行间距
测量杭高的工具： FastStone Capture

Mini Review
![文本属性总结.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/%E6%96%87%E6%9C%AC%E5%B1%9E%E6%80%A7%E6%80%BB%E7%BB%93.png)

## CSS 样式表

按照 CSS 样式书写的位置（或者引入的方式），CSS 样式表可以分为三大类：
![css引入方式总结.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/css%E5%BC%95%E5%85%A5%E6%96%B9%E5%BC%8F%E6%80%BB%E7%BB%93.png)

行内样式表（行内式）
内部样式表（嵌入式）
**外部样式表（链接式）**
引入外部样式表分为两步：
1. 新建一个后缀名为 `.css` 的样式文件，把所有 CSS 代码都放入此文件中，改文件中不需要标签。
2. 在 HTML 页面中，使用<link> 标签引入这个文件。 语法：

```html
 <link rel="stylesheet" href="css文件路径">
```

## Chrome 调试工具

帮助我们检查错误
1. Ctrl+ 滚轮 可以放大开发者工具代码大小。 
2. 左边是 HTML 元素结构，右边是 CSS 样式。 
3. 右边 CSS 样式可以改动数值（左右箭头或者直接输入）和查看颜色。 
4. Ctrl + 0 复原浏览器大小。 
5. 如果点击元素，发现右侧没有样式引入，极有可能是类名或者样式引入错误。 
6. 如果有样式，但是样式前面有黄色叹号提示，则是样式属性书写错误。