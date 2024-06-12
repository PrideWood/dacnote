---
date created: 2024-02-05T19:59:09+08:00
date modified: 2024-02-05T21:31:28+08:00
---
- 移动端基础
- 视口
- 二倍图
- 移动端调试
- 移动端技术解决方案
- 移动端常见布局

## 1. 移动端基础

- 移动端浏览器我们主要对 webkit 内核进行兼容
- 我们现在开发的移动端主要针对手机端开发
- 现在移动端碎片化比较严重，分辨率和屏幕尺寸大小不一
- 学会用谷歌浏览器模拟手机界面以及调试

## 2. 视口（viewport）

### 2.1 布局视口 layout viewport

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240205205712.png)

### 2.2 视觉视口 visual viewport

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240205205753.png)

### 2.3 理想视口 ideal viewport

- 需要手动添写 **meta 视口标签**通知浏览器操作
- meta 视口标签的主要目的：布局视口的宽度应该与理想视口的宽度一致，简单理解就是设备有多宽，我们布局的视口就多宽

### 2.4 小结

- 视口就是浏览器显示页面内容的屏幕区域
- 视口分为布局视口、视觉视口和理想视口
- 我们移动端布局想要的是理想视口就是手机屏幕有多宽，我们的布局视口就有多宽
- 想要理想视口，我们需要给我们的移动端页面添加 meta 视口标签

### 2.5 meta 视口标签

```html
<meta name="viewport" content="width=device-width, user-scalable=no,initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
```

| **属性**        | **解释说明**                             |
|---------------|--------------------------------------|
| width         | 宽度设置的是 viewport 宽度，可以设置 device-width 特殊值 |
| initial-scale | 初始缩放比，大于 0 的数字                         |
| maximum-scale | 最大缩放比，大于 0 的数字                         |
| minimum-scale | 最小缩放比，大于 0 的数字                         |
| user-scalable | 用户是否可以缩放，yes 或 no（1 或 0）                 |

### 2.6 标准的 viewport 设置

- 视口宽度和设备保持一致
- 视口的默认缩放比例 1.0
- 不允许用户自行缩放
- 最大允许的缩放比例 1.0
- 最小允许的缩放比例 1.0

## 3. 二倍图

### 3.1 物理像素&物理像素比

- 物理像素点指的是屏幕显示的最小颗粒，是物理真实存在的。这是厂商在出厂时就设置好了,比如苹果 6\7\8 是 750* 1334
- 我们开发时候的 1px 不是一定等于 1 个物理像素的
- PC 端页面，1 个 px 等于 1 个物理像素的，但是移动端就不尽相同
- 一个 px 的能显示的物理像素点的个数，称为物理像素比或屏幕像素比

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240205210933.png)

- PC 端 和 早前的手机屏幕 / 普通手机屏幕: 1CSS 像素 = 1 物理像素的
- Retina（视网膜屏幕）是一种显示技术，可以将把更多的物理像素点压缩至一块屏幕里，从而达到更高的分辨率，并提高屏幕显示的细腻程度。

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240205211029.png)

### 3.2 多倍图

- 对于一张 50px * 50px 的图片，在手机 Retina 屏中打开，按照刚才的物理像素比会放大倍数，这样会造成图片模糊
- 在标准的 viewport 设置中，使用倍图来提高图片质量，解决在高清设备中的模糊问题
- 通常使用二倍图， 因为 iPhone 6\7\8 的影响，但是现在还存在 3 倍图 4 倍图的情况，这个看实际开发公司需求
- 背景图片 注意缩放问题

```css
 /* 在 iphone8 下面 */
 img{
 /*原始图片100*100px*/
 width: 50px;
 height: 50px;
 } 
.box{
 /*原始图片100*100px*/
 background-size: 50px 50px;
 }
```

### 3.3 背景缩放 background-size

语法：

```css
background-size: 背景图片宽度 背景图片高度;
```

- 单位： 长度|百分比|cover|contain;
- cover 把背景图像扩展至足够大，以使背景图像完全覆盖背景区域。
- contain 把图像图像扩展至最大尺寸，以使其宽度和高度完全适应内容区域

### 3.4 多倍图切图 cutterman

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240205211314.png)

- @3X 3 倍图
- @2X 2 倍图
- @1X 1 倍图原图

## 4. 移动端开发选择

### 4.1 移动端主流方案

1. 单独制作移动端页面（主流）
	- 京东商城手机版
	- 淘宝触屏版
	- 苏宁易购手机版
	- ....

2. 响应式页面兼容移动端（其次）
	- 三星手机官网
	- ....

### 4.2 单独移动端页面（主流）

通常情况下，网址域名前面加 m(mobile) 可以打开移动端。通过判断设备，如果是移动设备打开，则跳到移动端页面。
- m.taobao.com
- m.jd.com
- m.suning.com

### 4.3 响应式兼容 PC 移动端

三星电子官网： www.samsung.com/cn/ ，通过判断屏幕宽度来改变样式，以适应不同终端。

缺点：制作麻烦， 需要花很大精力去调兼容性问题

## 5. 移动端技术解决方案

### 5.1 移动端浏览器

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240205211936.png)

### 5.2 CSS 初始化 normalize.css

- 保护了有价值的默认值
- 修复了浏览器的 bug
- 是模块化的
- 拥有详细的文档
官网地址： http://necolas.github.io/normalize.css/

### 5.3 CSS3 盒子模型 box-sizing

```css
 /*CSS3盒子模型*/
 box-sizing: border-box;
 /*传统盒子模型*/
 box-sizing: content-box;
```

- 移动端可以全部 CSS3 盒子模型，padding 和 border 不会撑大盒子
- PC 端如果完全需要兼容，我们就用传统模式，如果不考虑兼容性，我们就选择 CSS3 盒子模型

### 5.4 特殊样式

```css
 /*CSS3盒子模型*/
 box-sizing: border-box;
 -webkit-box-sizing: border-box;
 /*点击高亮我们需要清除清除 设置为transparent 完成透明*/
 -webkit-tap-highlight-color: transparent;
 /*在移动端浏览器默认的外观在iOS上加上这个属性才能给按钮和输入框自定义样式*/
 -webkit-appearance: none;
 /*禁用长按页面时的弹出菜单*/
 img,a { -webkit-touch-callout: none; }
```

## 6.移动端常见布局

1. 单独制作移动端页面（主流）
	- 流式布局（百分比布局）
	- flex 弹性布局（强烈推荐）
	- less+rem+ 媒体查询布局
	- 混合布局

2. 响应式页面兼容移动端（其次）
	- 媒体查询
	- bootstrap

### 6.1 流式布局（百分比布局）

- 流式布局，就是百分比布局，也称非固定像素布局。
- 通过盒子的宽度设置成百分比来根据屏幕的宽度来进行伸缩，不受固定像素的限制，内容向两侧填充。
- 流式布局方式是移动 web 开发使用的比较常见的布局方式。
- max-width 最大宽度 （max-height 最大高度） 
- min-width 最小宽度 （min-height 最小高度）

案例：[京东移动端首页](C:\Users\24742\Desktop\practice\MobieWeb\H5\index.html)

二倍精灵图做法
- 在 firework 里面把精灵图**等比例缩放为原来的一半** （不要再Fireworks里保存，否则会修改原图）
- 之后根据大小 测量坐标
- 注意代码里面 background-size 也要写： 精灵图原来宽度的一半

图片格式
- DPG 图片压缩技术
- webp 图片格式

Mini Review 移动端布局之流式布局
1. 标准 viewport 规范以及写法
2. 模拟移动端调试方法
3. 移动端常见的布局方案
4. 流式布局原理
5. 京东移动端首页布局技巧