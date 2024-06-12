---
date created: 2024-01-29T13:25:31+08:00
date modified: 2024-01-30T19:32:28+08:00
---

## PS 切图

### 1. 图层切图

最简单的切图方式：右击图层 → 导出 → 切片。

### 2. 切片切图

1. 利用切片选中图片：利用切片工具手动划出
2. 导出选中的图片：文件菜单 → 存储为 web 设备所用格式 → 选择我们要的图片格式 → 存储 。

### 3. PS 插件切图

Cutterman 是一款运行在 Photoshop 中的插件，能够自动将你需要的图层进行输出，以替代传统的手工 " 导出 web 所用格式 " 以及使用切片工具进行挨个切图的繁琐流程。

官网：[http://www.cutterman.cn/zh/cutterman](http://www.cutterman.cn/zh/cutterman)

注意：Cutterman 插件要求你的 PS 必须是完整版，不能是绿色版，所以大家需要安装完整版本。

## CSS 书写顺序

建议遵循以下顺序：

1. **布局定位属性**：display / position / float / clear / visibility / overflow（建议 display 第一个写，毕竟关系到模式）
2. **自身属性**：width / height / margin / padding / border / background
3. **文本属性**：color / font / text-decoration / text-align / vertical-align / white- space / break-word
4. **其他属性（CSS3）**：content / cursor / border-radius / box-shadow / text-shadow / background:linear-gradient …

**举例：**

```css
 .jdc {
    display: block;
    position: relative;
    float: left;
    width: 100px;
    height: 100px;
    margin: 0 10px;
    padding: 20px 0;
    font-family: Arial, 'Helvetica Neue', Helvetica, sans-serif;
    color: #333;
    background: rgba(0,0,0,.5);
    border-radius: 10px;
 } 
```

## 综合练习 - [学成在线首页](C:\Users\24742\Desktop\practice\study\index.html)

### 页面布局整体思路

1. 必须确定页面的**版心**（可视区），我们**测量**可得知；
2. 分析页面中的行模块，以及每个行模块中的列模块。其实页面布局第一准则；
3. 一行中的列模块经常浮动布局，先确定每个列的大小，之后确定列的位置。页面布局第二准则；
4. 制作 HTML 结构。我们还是遵循，先有结构，后有样式的原则。结构永远最重要；
5. 所以，先理清楚**布局结构**,再写代码尤为重要，这需要我们多写多积累。

### 页面制作

#### 确定版心

​	这个页面的版心是 1200 像素  ，每个版心都要水平居中对齐，所以，我们可以定义版心为公共类：

```css
.w {
    width: 1200px;
    margin: auto;
}
```

#### header 头部制作

**结构图如下：**

![1.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/1.png)

- 1 号是版心盒子 **header** 1200 * 42 的盒子水平居中对齐, 上下给一个 margin 值就好了。
- 版心盒子 里面包含 2 号盒子 **logo** 图标
- 版心盒子 里面包含 3 号盒子 **nav** 导航栏
- 版心盒子 里面包含 4 号盒子 **search** 搜索框
- 版心盒子 里面包含 5 号盒子 **user** 个人信息
- 注意，要求里面的 **4 个子盒子 必须都浮动**

**导航栏注意点:**

实际开发中，**重要的导航栏**，我们不会直接用链接 a ，而是**用 li 包含链接 (li+a) 的做法**

1. `li+a` 语义更清晰，一看这就是有条理的列表型内容。
2. 如果直接用 a，搜索引擎容易辨别为有堆砌关键字嫌疑（故意堆砌关键字容易被搜索引擎有降权的风险），从而影响网站排名

**注意:** 

1. 让导航栏一行显示, 给 li 加浮动，因为 li 是块级元素, 需要一行显示.
2. 这个 nav 导航栏可以不给宽度，将来可以继续添加其余文字
3. 因为导航栏里面文字不一样多，所以最好给链接 a 左右 padding 撑开盒子，而不是指定宽度 

**4 号盒子 search 的细节：**

​	search 搜索框的意思: 一个 search 大盒子里面包含 2 个 表单
​	技巧：input 和 button 都，属于行内块元素，会有缝隙，使用浮动，可以去缝隙。

#### banner 制作

![2.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/2.png)

- 1 号盒子是通栏的大盒子**banner**， 不给宽度，给高度，给一个蓝色背景。
- 2 号盒子是版心 **w**， 要水平居中对齐。
- 3 号盒子版心内，左对齐 **subnav** 侧导航栏。
- 4 号盒子版心内，右对齐 **course** 课程。

##### subnav 侧导航栏 (左侧的)

- subnav 盒子 背景色 黑色半透明
- 重要的导航栏，li 包 a ，行高 45px
- a 里面包含文字和 span，span 右浮动
- 当鼠标经过 a ，a 里面的内容（文字和 span）变蓝色

##### course 课程表模块 (右侧的)

![6.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/6.png)

- 1 号盒子 是 228 * 300 的盒子 右浮动 **注意 浮动的元素 不会有外边距塌陷的问题**
- 1 号盒子内 分为 上下 两个 子盒子
- 2 号子盒子是 上部分 我们命名为 course-hd (hd 是 head 的简写 头部的意思，我们经常用)
- 3 号子盒子是 下部分 我们命名为 course-bd (bd 是 body 的简写 主体的意思，我们经常用)

#### 精品推荐小模块

结构图如下：
![3.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/3.png)

- **复习点：** 因为里面三个盒子都要垂直居中，我们利用 继承性，给 最大的盒子 一个垂直居中的代码就好了，还记得 那些 样式可以继承吗？？？ font- line- text- color
    
- 大盒子水平居中 goods 精品 ，注意此处有个盒子阴影
- 1 号盒子是标题 H3 左侧浮动
- 2 号盒子 里面放链接 左侧浮动 goods-item 距离可以控制链接的 左右外边距（注意行内元素只给左右内外边距）
- 3 号盒子 右浮动 mod 修改

#### 精品推荐大模块

结构图如下：
![4.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/4.png)

- 1 号盒子为最大的盒子 **box**  版心水平居中对齐
- 2 号盒子为上面部分 **box-hd**  -- 里面   左侧标题 H3 左浮动   右侧 链接 a 右浮动
- 3 号盒子为底下部分 **box-bd** --- 里面是无序列表 有 10 个 小 li 组成
- 小 li 外边距的问题， 这里有个小技巧。  给 box-hd 宽度为 1215 就可以一行装开 5 个 li 了
- 复习点：我们用到清除浮动，因为 box-hd 里面的盒子个数不一定是多少，所以我们就不给高度了，但是里面的盒子浮动会影响下面的布局，因此需要清除浮动。

#### 底部模块制作

结构图如下：

![](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/5.png)

- 1 号盒子通栏大盒子 底部 **footer** 给高度 底色是白色
- 2 号盒子版心水平居中
- 3 号盒子版权 **copyright** 左对齐
- 4 号盒子 链接组 **links** 右对齐