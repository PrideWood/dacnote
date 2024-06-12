---
date created: 2024-02-01T20:34:22+08:00
date modified: 2024-02-05T19:56:28+08:00
---
![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240201205225.png)

**VS code 使用技巧**
`Alt + shift + ↑/↓` 快捷复制一行到上一行或下一行
插件 Auto Rename Tag 自动重命名配对的 HTML/XML 标签
CSS Peek 追踪至样式

## 1. CSS 2D 转换（transform）

- 移动：translate
- 旋转：roatate
- 缩放：scale

### 网页中的二维坐标系

![image.png|400](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240204132615.png)

### 1.1 移动 translate

![image.png|200](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240204134607.png)

**语法**

```css
transform: translate(x,y); 
/*或者分开写*/
transform: translateX(n);
transform: translateY(n);
```

特点：
1. 定义 2D 转换中的移动，沿着 X 和 Y 轴移动元素
2. translate 最大的优点：**不会影响到其他元素的位置**
3. translate 中的**百分比单位是相对于自身元素**的 `translate:(50%,50%);`
4. 对行内标签没有效果

应用：让一个盒子水平垂直居中

### 1.2 旋转 rotate

![image.png|200](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240204134713.png)

语法

```css
transform:rotate(度数)
```

特点
- rotate 里面跟度数， 单位是 deg 比如 `rotate(45deg)`
- 角度为正时，顺时针，负时，为逆时针
- 默认旋转的中心点是元素的中心点

应用：下拉列表小箭头
方形的相邻两边再旋转
![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240204141725.png)

[示例代码](C:\Users\24742\Desktop\practice\MobieWeb\CSS3-rotate.html)：

```css
p::before {
	content: '';
	position: absolute;
	right: 20px;
	top: 10px;
	width: 10px;
	height: 10px;
	border-right: 1px solid #000;
	border-bottom: 1px solid #000;
	transform: rotate(45deg);
}
```

### 1.3 换中心点 transform-origin

语法

```css
transform-origin: x y;
```

特点
- 注意后面的参数 x 和 y 用空格隔开
- x y 默认转换的中心点是元素的中心点 (50% 50%)/(center center)
- 还可以给 x y 设置 像素 或者 方位名词 （top bottom left right center）

### 1.4 缩放 scale

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240204141852.png)

语法

```css
transform:scale(x,y);
```

特点：
注意其中的 x 和 y **用逗号分隔**
- `transform:scale(1,1)` ：宽和高都放大一倍，相对于没有放大
- `transform:scale(2,2)`：宽和高都放大了 2 倍
- `transform:scale(2)` ：只写一个参数，第二个参数则和第一个参数一样，相当于 `scale(2,2)`
- `transform:scale(0.5,0.5)`：缩小
- sacle 缩放最大的优势：可以设置转换中心点缩放，**默认以中心点缩放的，而且不影响其他盒子**

应用：分页按钮

### 综合写法

注意：
1. 同时使用多个转换，其格式为：`transform: translate() rotate() scale() ...` 等，
2. 其**顺序**会影转换的效果。（先旋转会改变坐标轴方向）
3. 当我们同时有位移和其他属性的时候，记得要将**位移放到最前**

### Mini Review

- 转换 transform 我们简单理解就是变形 有 2D 和 3D 之分
- 我们暂且学了三个 分别是 位移 旋转 和 缩放
- 2D 移动 translate(x, y) 最大的优势是不影响其他盒子， 里面参数用%，是相对于自身宽度和高度来计算的
- 可以分开写比如 translateX(x) 和 translateY(y)
- 2D 旋转 rotate(度数) 可以实现旋转元素 度数的单位是 deg
- 2D 缩放 sacle(x,y) 里面参数是数字 不跟单位 可以是小数 最大的优势 不影响其他盒子
- 设置转换中心点 transform-origin : x y; 参数可以百分比、像素或者是方位名词，注意用 x 和 y 空格隔开
- 当我们进行综合写法，同时有位移和其他属性的时候，记得要将位移放到最前

## 2. CSS 动画（animation）

### 2.1 动画的基本使用

1. 先定义动画
2. 再使用（调用）动画

#### 1. 用 keyframes 定义动画（类似定义类选择器）

```css
@keyframes 动画名称 {
 0% {
 width:100px;
 } 
 100% {
 width:200px;
 }
}
```

**说明：动画序列**
- 0% 是动画的开始，100% 是动画的完成。这样的规则就是动画序列。
- 在 @keyframes 中规定某项 CSS 样式，就能创建由当前样式逐渐改为新样式的动画效果。
- 动画是使元素从一种样式逐渐变化为另一种样式的效果。您可以改变任意多的样式任意多的次数。
- 请用百分比来规定变化发生的时间，或用关键词 "from" 和 "to"，等同于 0% 和 100%（百分比就是时间的划分）。

#### 2. 元素使用动画

```css
div {
 width: 200px;
 height: 200px;
 background-color: aqua;
 margin: 100px auto;
 /* 调用动画 */
 animation-name: 动画名称;
 /* 持续时间 */
 animation-duration: 持续时间;
 }
```

### 2.2 动画常用属性

| **属性**                    | **描述**                                   |
|---------------------------|------------------------------------------|
| @keyframes                | 规定动画。                                    |
| animation                 | 所有动画属性的简写属性，除了 animation-play-state 属性。    |
| animation-name            | 规定@keyframes 动画的名称。（必须的）                  |
| animation-duration        | 规定动画完成一个周期所花费的秒或毫秒，默认是 0。（必须的）            |
| animation-timing-function | 规定动画的速度曲线，默认是“ease”。                     |
| animation-delay           | 规定动画何时开始，默认是 0。                           |
| animation-iteration-count | 规定动画被播放的次数，默认是 1，还有 infinite               |
| animation-direction       | 规定动画是否在下一周期逆向播放，默认是“normal“，alternate 逆播放 |
| animation-play-state      | 规定动画是否正在运行或暂停。默认是 "running"，还有 "paused"。   |
| animation-fill-mode       | 规定动画结束后状态，保持 forwards 回到起始 backwards        |

### 2.3 动画简写属性

语法：前两个属性一定要写

```css
animation：动画名称 持续时间 运动曲线 何时开始 播放次数 是否反方向 动画起始或者结束的状态;
```

示例代码：

```css
animation: myfirst 5s linear 2s infinite alternate;
```

特点：
- 简写属性里面**不包含** animation-play-state 
- 暂停动画：animation-play-state: puased; 经常和鼠标经过等其他配合使用
- 想要动画走回来 ，而不是直接跳回来：animation-direction: alternate
- 盒子动画结束后，停在结束位置： animation-fill-mode: forwards

应用：热点图

### 2.4 速度曲线细节

语法：

```css
animation-timing-function：规定动画的速度曲线，默认是“ease”
```

| **值**       | **描述**                  |
|-------------|-------------------------|
| linear      | 动画从头到尾的速度是相同的。匀速        |
| ease        | 默认。动画以低速开始，然后加快，在结束前变慢。 |
| ease-in     | 动画以低速开始。                |
| ease-out    | 动画以低速结束。                |
| ease-in-out | 动画以低速开始和结束。             |
| steps()     | 指定了时间函数中的间隔数量（步长）       |

steps 可以用来做打字机效果，配合溢出隐藏使用
案例：[奔跑的小熊](C:\Users\24742\Desktop\practice\MobieWeb\CSS3-奔跑小熊.html)

## 3. 3D 转换

3D 效果特点
- 近大远小
- 物体后面遮挡不可见

### 3.1 三维坐标系

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240204144544.png)

- x 轴：水平向右 注意： x 右边是正值，左边是负值
- y 轴：垂直向下 注意： y 下面是正值，上面是负值
- z 轴：垂直屏幕 注意： 往外面是正值，往里面是负值

常见效果
- 3D 位移: translate3d(x,y,z)
- 3D 旋转: rotate3d(x,y,z)
- 透视: perspective
- 3D 呈现 transfrom-style

### 3.2 3D 移动 translate3d

3D 移动在 2D 移动的基础上多加了一个可以移动的方向，就是 z 轴方向。
- `translform:translateX(100px)`：仅仅是在 x 轴上移动
- `translform:translateY(100px)`：仅仅是在 Y 轴上移动
- `translform:translateZ(100px)`：仅仅是在 Z 轴上移动（注意：translateZ 一般用 px 单位）
- `transform:translate3d(x,y,z)`：其中 x、y、z 分别指要移动的轴的方向的距离 因为 z 轴是垂直屏幕，由里指向外面，所以默认是看不到元素在 z 轴的方向上移动

### 3.3 透视 perspective

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240204144920.png)

在 2D 平面产生近大远小视觉立体，但是只是效果二维的
- 如果想要在网页产生 3D 效果需要透视（理解成 3D 物体投影在 2D 平面内）。
- 模拟人类的视觉位置，可认为安排一只眼睛去看 - 透视我们也称为视距：视距就是人的眼睛到屏幕的距离
- 距离视觉点越近的在电脑平面成像越大，越远成像越小 - 透视的单位是像素
透视**写在被观察元素的父盒子上**面的
d：就是视距，视距就是一个距离人的眼睛到屏幕的距离。
z：就是 z 轴，物体距离屏幕的距离，z 轴越大（正值） 我们看到的物体就越大。

### 3.4 translateZ

translform:translateZ(100px)：仅仅是在 Z 轴上移动。
有了透视，就能看到 translateZ 引起的变化了 - translateZ：近大远小
- translateZ：往外是正值
- translateZ：往里是负值

### 3.5 3D 旋转 rotate3d

3D 旋转指可以让元素在三维平面内沿着 x 轴，y 轴，z 轴或者自定义轴进行旋转。

语法
- `transform:rotateX(45deg)`：沿着 x 轴正方向旋转 45 度
- `transform:rotateY(45deg)` ：沿着 y 轴正方向旋转 45deg
- `transform:rotateZ(45deg)` ：沿着 Z 轴正方向旋转 45deg
- `transform:rotate3d(x,y,z,deg)`： 沿着自定义轴旋转 deg 为角度（了解即可）

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240204145442.png)

左手准则
- 左手的手拇指指向 x 轴（y 轴）的正方向 - 其余手指的弯曲方向就是该元素沿着 x 轴（y 轴）旋转的方向

`transform:rotate3d(x,y,z,deg)`： 沿着自定义轴旋转 deg 为角度（了解即可）
xyz 是表示**旋转轴的矢量**，是标示你是否希望沿着该轴旋转，最后一个标示旋转的角度。
- `transform:rotate3d(1,0,0,45deg)` 就是沿着 x 轴旋转 45deg
- `transform:rotate3d(1,1,0,45deg)` 就是沿着对角线旋转 45deg

### 3.6 3D 呈现 transfrom-style ※

- 控制子元素是否开启三维立体环境。。
- transform-style: flat 子元素不开启 3d 立体空间 默认的
- `transform-style: preserve-3d;` 子元素开启立体空间
- **代码写给父级，但是影响的是子盒子**
- 这个属性很重要，后面必用

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240204150017.png)

案例 1：[两面翻转的盒子](C:\Users\24742\Desktop\practice\MobieWeb\CSS3-翻转盒子.html)

案例 2：[3D 导航栏](C:\Users\24742\Desktop\practice\MobieWeb\CSS3-3D导航栏.html)

案例 3：[旋转木马](C:\Users\24742\Desktop\practice\MobieWeb\CSS3-旋转木马.html)

## 浏览器私有前缀

浏览器私有前缀是为了**兼容老版本**的写法，比较新版本的浏览器无须添加。

1. 私有前缀
- -moz-：代表 firefox 浏览器私有属性
- -ms-：代表 ie 浏览器私有属性
- -webkit-：代表 safari、chrome 私有属性
- -o-：代表 Opera 私有属性

1. 提倡的写法

```css
-moz-border-radius: 10px; 
-webkit-border-radius: 10px; 
-o-border-radius: 10px; 
border-radius: 10px;
```
