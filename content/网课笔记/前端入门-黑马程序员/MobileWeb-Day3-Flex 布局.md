---
date created: 2024-02-05T21:36:09+08:00
date modified: 2024-02-08T10:57:42+08:00
---
- flex 布局体验
- flex 布局原理
- flex 布局父项常见属性
- flex 布局子项常见属性
- 携程网首页案例制作

## 1. flex 布局体验

传统布局
- 兼容性好
- 布局繁琐
- 局限性，不能再移动端很好的布局

flex 弹性布局
- 操作方便，布局极为简单，移动端应用很广泛
- PC 端浏览器支持情况较差
- IE 11 或更低版本，不支持或仅部分支持

## 2. flex 布局原理

### 2.1 布局原理

flex 是 flexible Box 的缩写，意为 " 弹性布局 "，用来为盒状模型提供最大的灵活性，任何一个容器都可以
指定为 flex 布局。
- 当我们为父盒子设为 flex 布局以后，子元素的 float、clear 和 vertical-align 属性将失效。
- 伸缩布局 = 弹性布局 = 伸缩盒布局 = 弹性盒布局 =flex 布局

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240205214242.png)

采用 Flex 布局的元素，称为 Flex 容器（flex container），简称 " 容器 "。它的所有子元素自动成为容器成员，称为 Flex 项目（flex item），简称 " 项目 "。
- 体验中 div 就是 flex 父容器。
- 体验中 span 就是 子容器 flex 项目
- 子容器可以横向排列也可以纵向排列（沿主轴方向）
总结 flex 布局原理：
就是**通过给父盒子添加 flex 属性，来控制子盒子的位置和排列方式**

## 3. flex 布局父项常见属性

### 3.1 常见父项属性

以下由 6 个属性是对父元素设置的
- flex-direction：设置主轴的方向
- justify-content：设置主轴上的子元素排列方式
- flex-wrap：设置子元素是否换行 
- align-content：设置侧轴上的子元素的排列方式（多行）
- align-items：设置侧轴上的子元素排列方式（单行）
- flex-flow：复合属性，相当于同时设置了 flex-direction 和 flex-wrap

### 3.2 flex-direction 设置主轴的方向

#### 1. 主轴与侧轴

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240205214458.png)

### 2. 属性值

| **属性值**        | **说明**  |
|----------------|---------|
| row            | 默认值从左到右 |
| row-reverse    | 从右到左    |
| column         | 从上到下    |
| column-reverse | 从下到上    |

### 3.3 justify-content 设置主轴上的子元素排列方式

注意： 使用这个属性之前一定要**确定好主轴**是哪个

| **属性值**       | **说明**                  |
|---------------|-------------------------|
| flex-start    | 默认值 从头部开始 如果主轴是 x 轴，则从左到右 |
| flex-end      | 从尾部开始排列                 |
| center        | 在主轴居中对齐（如果主轴是 x 轴则 水平居中）  |
| space-around  | 平分剩余空间                  |
| space-between | 先两边贴边 再平分剩余空间（重要）       |

### 3.4 flex-wrap 设置子元素是否换行

默认显示不下时，缩小子盒子的大小。

| **属性值** | **说明**  |
|---------|---------|
| nowrap  | 默认值，不换行 |
| wrap    | 换行      |

### 3.5 align-items 设置侧轴上的子元素排列方式（单行 ）

| **属性值**    | **说明**       |
|------------|--------------|
| flex-start | 从上到下         |
| flex-end   | 从下到上         |
| center     | 挤在一起居中（垂直居中） |
| stretch    | 拉伸 （默认值 ）    |

### 3.6 align-content 设置侧轴上的子元素的排列方式（多行）

设置子项在侧轴上的排列方式，并且只能用于子项出现**换行**（`flex-wrap: wrap;`) 的情况（多行），在单行下是没有效果的。

| **属性值**       | **说明**              |
|---------------|---------------------|
| flex-start    | 默认值在侧轴的头部开始排列       |
| flex-end      | 在侧轴的尾部开始排列          |
| center        | 在侧轴中间显示             |
| space-around  | 子项在侧轴平分剩余空间         |
| space-between | 子项在侧轴先分布在两头，再平分剩余空间 |
| stretch       | 设置子项元素高度平分父元素高度     |

**align-content 和 align-items 区别**
- align-items 适用于单行情况下， 只有上对齐、下对齐、居中和 拉伸
- align-content 适应于换行（多行）的情况下（单行情况下无效）， 可以设置 上对齐、 下对齐、居中、拉伸以及平均分
配剩余空间等属性值。
- 总结就是单行找 align-items 多行找 align-content

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240205215141.png)

### 3.7 flex-flow

flex-flow 属性是 flex-direction 和 flex-wrap 属性的复合属性

```css
flex-flow:row wrap;
```

- flex-direction：设置主轴的方向
- justify-content：设置主轴上的子元素排列方式
- flex-wrap：设置子元素是否换行 
- align-content：设置侧轴上的子元素的排列方式（多行）
- align-items：设置侧轴上的子元素排列方式（单行）
- flex-flow：复合属性，相当于同时设置了 flex-direction 和 flex-wrap

## 4. flex 布局子项常见属性

- flex 子项目占的份数
- align-self 控制子项自己在侧轴的排列方式
- order 属性定义子项的排列顺序（前后顺序）

### 4.1 flex 属性

flex 属性定义子项目分配**剩余空间**，用 flex 来表示占多少份数。

```css
.item {
 flex: <number>; /* default 0 */
}
```

### 4.2 align-self 控制子项自己在侧轴上的排列方式

align-self 属性**允许单个项目有与其他项目不一样**的对齐方式，可覆盖 align-items 属性。
默认值为 auto，表示继承父元素的 align-items 属性，如果没有父元素，则等同于 stretch。

```css
span:nth-child(2) {
 /* 设置自己在侧轴上的排列方式 */
 align-self: flex-end;
 }
```

### 4.3 order 属性定义项目的排列顺序

数值越小，排列越靠前，默认为 0。
注意：和 z-index 不一样。

```css
.item {
 order: <number>;
}
```

## 5. [携程网首页案例](C:\Users\24742\Desktop\practice\MobieWeb\ctrip\index.html)

### 模块的划分及命名

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240207101940.png)
![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240207101957.png)

### 常见 Flex 布局思路

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240207103833.png)

### 利用属性选择器更换背景图片

- 命名是用有语义的词汇 + 数字命名，如 local-nav-icon1, local-nav-icon2...
- 这样可以用属性选择器选择出来，如 `.local-nav li [class^=".local-nav-icon"]`
- 之后单独设置各个部分不同的样式，注意权重问题，选择器名称写全
- 如果精灵图上图标的排列有规律可以按照其坐标快速修改 background-position 的值

### 背景渐变

[线性渐变](C:\Users\24742\Desktop\practice\MobieWeb\CSS3-线性渐变效果.html)

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240208095200.png)

语法：

```css
background: linear-gradient(起始方向, 颜色1, 颜色2, ...);
background: -webkit-linear-gradient(left, red , blue);
background: -webkit-linear-gradient(left top, red , blue);
```

背景渐变必须添加浏览器私有前缀
起始方向可以是： 方位名词 或者 度数 ， 如果省略默认就是 top
