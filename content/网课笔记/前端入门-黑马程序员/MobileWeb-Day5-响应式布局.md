---
date created: 2024-02-08T11:58:34+08:00
date modified: 2024-02-11T10:30:11+08:00
---
- 响应式开发
- Bootstrap 前端开发框架
- Bootstrap 栅格系统
- 阿里百秀首页案例

## 1. 响应式开发

### 1.1 响应式开发原理

就是使用媒体查询针对不同宽度的设备进行布局和样式的设置，从而适配不同设备的目的。

| **设备划分** | **尺寸区间** |
| ---- | ---- |
| 超小屏幕（手机） | < 768px |
| 小屏设备（平板） | >= 768px ~ < 992px |
| 中等屏幕（桌面显示器） | >= 992px ~ <1200px |
| 宽屏设备（大桌面显示器） | >= 1200px |

### 1.2 响应式布局容器

响应式需要一个父级做为布局容器，来配合子级元素来实现变化效果。原理就是在不同屏幕下，通过媒体查询来改变这个布局容器的大小，再改变里面子元素的排列方式和大小，从而实现不同屏幕下，看到不同的页面布局和样式变化。

平时我们的响应式尺寸划分
- 超小屏幕（手机，小于 768px）：设置宽度为 100%
- 小屏幕（平板，大于等于 768px）：设置宽度为 750px
- 中等屏幕（桌面显示器，大于等于 992px）：宽度设置为 970px
- 大屏幕（大桌面显示器，大于等于 1200px）：宽度设置为 1170px 

但是我们也可以根据实际情况自己定义划分

案例：响应式导航

## 2. Bootstrap 前端开发框架

### 2.1 Bootstrap 简介

Bootstrap 来自 Twitter（推特），是目前最受欢迎的前端框架。Bootstrap 是基于 HTML、CSS 和 JAVASCRIPT 的，它
简洁灵活，使得 Web 开发更加快捷。
- 中文官网： http://www.bootcss.com/
- 官网： http://getbootstrap.com/
- 推荐使用： http://bootstrap.css88.com/ 
框架：顾名思义就是一套架构，它有一套比较完整的网页功能解决方案，而且控制权在框架本身，有预制样式库、组件和
插件。使用者要按照框架所规定的某种规范进行开发。

优点
- 标准化的 html+css 编码规范
- 提供了一套简洁、直观、强悍的组件
- 有自己的生态圈，不断的更新迭代
- 让开发更简单，提高了开发的效率

版本
- 2.x.x：停止维护,兼容性好,代码不够简洁，功能不够完善。
- 3.x.x：目前使用最多,稳定,但是放弃了 IE6-IE7。对 IE8 支持但是界面效果不好,偏向用于开发响应式布局、移动设备优先的 WEB 项目。
- 4.x.x ：最新版，目前还不是很流行

### 2.2 Bootstrap 使用

在现阶段我们还没有接触 JS 相关课程，所以我们只考虑使用它的样式库。
控制权在框架本身，使用者要按照框架所规定的某种规范进行开发。
Bootstrap 使用四步曲： 
1. 创建文件夹结构
2. 创建 html 骨架结构
3. 引入相关样式文件
4. 书写内容

创建 html 骨架结构

```html
<!--要求当前网页使用IE浏览器最高版本的内核来渲染-->
 <meta http-equiv="X-UA-Compatible" content="IE=edge">
<!--视口的设置：视口的宽度和设备一致，默认的缩放比例和PC端一致，用户不能自行缩放-->
 <meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=0">
 <!--[if lt IE 9]>
 <!--解决ie9以下浏览器对html5新增标签的不识别，并导致CSS不起作用的问题-->
 <script src="https://oss.maxcdn.com/html5shiv/3.7.2/html5shiv.min.js"></script>
 <!--解决ie9以下浏览器对 css3 Media Query 的不识别 -->
 <script src="https://oss.maxcdn.com/respond/1.4.2/respond.min.js"></script>
 <![endif]-->
```

引入相关样式文件

```html
<!-- Bootstrap 核心样式-->
<link rel="stylesheet" href="bootstrap/css/bootstrap.min.css">
```

### 2.3 布局容器

Bootstrap 需要为页面内容和栅格系统包裹一个 .container 容器，它提供了两个作此用处的类。

1. container 类
- 响应式布局的容器 固定宽度
- 大屏 ( >=1200px) 宽度定为 1170px
- 中屏 ( >=992px) 宽度定为 970px
- 小屏 ( >=768px) 宽度定为 750px
- 超小屏 (100%)

2. container-fluid 类
- 流式布局容器 百分百宽度
- 占据全部视口（viewport）的容器。

## 3. Bootstrap 栅格系统

### 3.1 栅格系统简介

栅格系统英文为“grid systems”,也有人翻译为“网格系统”，它是指将页面布局划分为等宽的列，然后通过列数的定义来模块化页面布局。
Bootstrap 提供了一套响应式、移动设备优先的流式栅格系统，随着屏幕或视口（viewport）尺寸的增加，系统会自动分为最多 12 列。

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240208121232.png)

### 3.2 栅格选项参数

栅格系统用于通过一系列的行（row）与列（column）的组合来创建页面布局，你的内容就可以放入这些创建好的布局中。

|             | **超小屏幕（手机）< 768px** | **小屏设备（平板）>=768px** | **中等屏幕（桌面显示器）>=992px** | **宽屏设备（大桌面显示器）>=1200px** |
|-----------------|---------------------|---------------------|------------------------|--------------------------|
| .container 最大宽度 | 自动 (100%)            | 750px               | 970px                  | 1170px                   |
| 类前缀             | .col-xs-            | .col-sm-            | .col-md-               | .col-lg-                 |
| 列（column）数      |                     |                     | 12                     |                          |

- 按照不同屏幕划分为 1~12 等份
- 行（row） 必须放到 container 布局容器里面
- 行（row） 可以去除父容器作用 15px 的边距
- 要实现列的平均分配需要给列添加类前缀
- 不需要媒体查询，直接使用：xs-extra small：超小； sm-small：小； md-medium：中等； lg-large：大；
- 列（column）大于 12，多余的“列（column）”所在的元素将被作为一个整体另起一行排列
- 每一列默认有左右 15 像素的 padding
- 可以同时为一列指定多个设备的类名，以便划分不同份数 例如 class="col-md-4 col-sm-6"

### 3.3 列嵌套

栅格系统内置的栅格系统将内容再次嵌套。简单理解就是一个列内再分成若干份小列。我们可以通过添加一个新的 .row 元素和一系列 `.col-sm-*` 元素到已经存在的 `.col-sm-*` 元素内

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240208121659.png)

实现代码

```html
<!-- 列嵌套 -->
 <div class="col-sm-4">
 <!-- 列嵌套最好加1个行row这样可以取消父级元素的padding值，而且自动和父级元素一样高 -->
 <div class="row">
 <div class="col-sm-6">小列</div>
 <div class="col-sm-6">小列</div>
 </div>
</div>
```

### 3.4 列偏移

使用 `.col-md-offset-*` 类可以将列向右侧偏移。这些类实际是通过使用 * 选择器为当前元素增加了左侧的边距（margin）

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240208121821.png)

实现代码：

```html
 <!-- 列偏移 -->
 <div class="row">
 <div class="col-lg-4">1</div>
 <div class="col-lg-4 col-lg-offset-4">2</div>
 </div>
```

### 3.5 列排序

通过使用 `.col-md-push-*` 和 `.col-md-pull-*` 类就可以很容易的改变列（column）的顺序。
向左是拉，向右是推

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240208121936.png)

```html
 <!-- 列排序 -->
 <div class="row">
 <div class="col-lg-4 col-lg-push-8">左侧</div>
 <div class="col-lg-8 col-lg-pull-4">右侧</div>
 </div>
```

### 3.6 响应式工具

为了加快对移动设备友好的页面开发工作，利用媒体查询功能，并使用这些工具类可以方便的针对不同设备展示或隐藏页面内容

| **类名**     | **超小屏** | **小屏** | **中屏** | **大屏** |
|------------|---------|--------|--------|--------|
| .hidden-xs | 隐藏      | 可见     | 可见     | 可见     |
| .hidden-sm | 可见      | 隐藏     | 可见     | 可见     |
| .hidden-md | 可见      | 可见     | 隐藏     | 可见     |
| .hidden-lg | 可见      | 可见     | 可见     | 隐藏     |

只在某特定屏幕展示内容，如：

```html
<span class="visible-lg">在大屏显示这句话</span>
```

Bootstrap 其他（按钮、表单、表格） 请参考 Bootstrap 文档。

## 4. [阿里百秀](C:\Users\24742\Desktop\practice\MobieWeb\alibaixiu\index.html)首页案例

页面布局分析

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240208122247.png)


