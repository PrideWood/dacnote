---
date created: 2024-02-23T19:17:19+08:00
date modified: 2024-02-23T20:27:10+08:00
---
## 客户端与服务器

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240223192157.png)

## URL 地址

URL（全称是 UniformResourceLocator）中文叫统一资源定位符，用于标识互联网上每个资源的唯一存放位置。浏览器只有通过 URL 地址，才能正确定位资源的存放位置，从而成功访问到对应的资源。

url 的组成部分

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240223192335.png)

## 分析网页的打开过程

- 客户端与服务器之间的通信过程，分为 请求 – 处理 – 响应 三个步骤。
- 网页中的每一个资源，都是通过 请求 – 处理 – 响应 的方式从服务器获取回来的。

基于浏览器的开发者工具分析通信过程

1. 打开 Chrome 浏览器
2. Ctrl+Shift+I 打开 Chrome 的开发者工具
3. 切换到 Network 面板
4. 选中 Doc 页签
5. 刷新页面，分析客户端与服务器的通信过程

## 服务器对外提供了哪些资源

常见的网页资源有文字、图片、音频、视频等。

数据，也是服务器对外提供的一种资源。只要是资源，必然要通过 请求 – 处理 – 响应 的方式进行获取。

如果要在网页中请求服务器上的数据资源，则需要用到 XMLHttpRequest 对象。
XMLHttpRequest（简称 xhr）是浏览器提供的 js 成员，通过它，可以请求服务器上的数据资源。
最简单的用法 `var xhrObj = new XMLHttpRequest()`

### 资源的请求方式

客户端请求服务器时，请求的方式有很多种，最常见的两种请求方式分别为 get 和 post 请求。

 get 请求通常用于获取服务端资源（向服务器要资源）
      例如：根据 URL 地址，从服务器获取 HTML 文件、css 文件、js 文件、图片文件、数据资源等

 post 请求通常用于向服务器提交数据（往服务器发送资源）
      例如：登录时向服务器提交的登录信息、注册时向服务器提交的注册信息、添加用户时向服务器提交的用户信息等各种数据提交操作

## 了解 Ajax

Ajax 的全称是 Asynchronous Javascript and XML（异步 JavaScript 和 XML）。
通俗的理解：在网页中利用 XMLHttpRequest 对象和服务器进行**数据交互**的方式，就是 Ajax。

Ajax 的典型应用场景
- 用户名检测：注册用户时，通过 ajax 的形式，动态检测用户名是否被占用
- 搜索提示：当输入搜索关键字时，通过 ajax 的形式，动态加载搜索提示列表
- 数据分页显示：当点击页码值的时候，通过 ajax 的形式，根据页码值动态刷新表格的数据
- 数据的增删改查：数据的添加、删除、修改、查询操作，都需要通过 ajax 的形式，来实现数据的交互

## jQuery 中的 Ajax

浏览器中提供的 XMLHttpRequest 用法比较复杂，所以 jQuery 对 XMLHttpRequest 进行了封装，提供了一系列 Ajax 相关的函数，极大地降低了 Ajax 的使用难度。
jQuery 中发起 Ajax 请求最常用的三个方法如下：
- `$.get()`
- `$.post()`
- `$.ajax()`

### $.get() 函数

jQuery 中 $.get() 函数的功能单一，专门用来发起 get 请求，从而将服务器上的资源请求到客户端来进行使用。

$.get() 函数的语法如下：

```js
$.get(url, [data], [callback])
```

三个参数各自代表的含义如下：

| **参数名**  | **参数类型** | **是否必选** | **说明**       |
|----------|----------|----------|--------------|
| url      | string   | 是        | 要请求的资源地址     |
| data     | object   | 否        | 请求资源期间要携带的参数 |
| callback | function | 否        | 请求成功时的回调函数   |

使用 $.get() 函数发起不带参数的请求时，直接提供请求的 URL 地址和请求成功之后的回调函数即可，示例代码如下：

```js
$.get('http://www.liulongbin.top:3006/api/getbooks', function(res) {
    console.log(res) // 这里的 res 是服务器返回的数据
})
```

使用 $.get() 函数发起带参数的请求时，示例代码如下：

```js
$.get('http://www.liulongbin.top:3006/api/getbooks', { id: 1 }, function(res) {
    console.log(res)
})
```

### $.post() 函数

jQuery 中 $.post() 函数的功能单一，专门用来发起 post 请求，从而向服务器提交数据。
$.post() 函数的语法如下：

```js
$.post(url, [data], [callback])
```

三个参数各自代表的含义如下：

| **参数名**  | **参数类型** | **是否必选** | **说明**       |
| -------- | -------- | -------- | ------------ |
| url      | string   | 是        | 提交数据的地址      |
| data     | object   | 否        | 要提交的数据       |
| callback | function | 否        | 数据提交成功时的回调函数 |

示例代码

```js
$.post(
   'http://www.liulongbin.top:3006/api/addbook', // 请求的URL地址
   { bookname: '水浒传', author: '施耐庵', publisher: '上海图书出版社' }, // 提交的数据
   function(res) { // 回调函数
      console.log(res)
   }
)
```

### $.ajax() 函数

相比于 $.get() 和 $.post() 函数，jQuery 中提供的 $.ajax() 函数，是一个功能比较综合的函数，它允许我们对 Ajax 请求进行更详细的配置。
$.ajax() 函数的基本语法如下：

```js
$.ajax({
   type: '', // 请求的方式，例如 GET 或 POST
   url: '',  // 请求的 URL 地址
   data: { },// 这次请求要携带的数据
   success: function(res) { } // 请求成功之后的回调函数
})
```

使用 $.ajax() 发起 GET 请求时，只需要将 type 属性的值设置为 'GET' 即可：

```js
$.ajax({
   type: 'GET', // 请求的方式
   url: 'http://www.liulongbin.top:3006/api/getbooks',  // 请求的 URL 地址
   data: { id: 1 },// 这次请求要携带的数据
   success: function(res) { // 请求成功之后的回调函数
       console.log(res)
   }
})
```

使用 $.ajax() 发起 POST 请求时，只需要将 type 属性的值设置为 'POST' 即可：

```js
$.ajax({
   type: 'POST', // 请求的方式
   url: 'http://www.liulongbin.top:3006/api/addbook',  // 请求的 URL 地址
   data: { // 要提交给服务器的数据
      bookname: '水浒传',
      author: '施耐庵',
      publisher: '上海图书出版社'
    },
   success: function(res) { // 请求成功之后的回调函数
       console.log(res)
   }
})
```

## 接口

使用 Ajax 请求数据时，被请求的 URL 地址，就叫做数据接口（简称接口）。同时，每个接口必须有请求方式。
例如：
http://www.liulongbin.top:3006/api/getbooks 获取图书列表的接口 (GET 请求)
http://www.liulongbin.top:3006/api/addbook 添加图书的接口（POST 请求）

### 接口测试工具 PostMan

为了验证接口能否被正常被访问，我们常常需要使用接口测试工具，来对数据接口进行检测。
好处：接口测试工具能让我们在不写任何代码的情况下，对接口进行调用和测试。

PostMan 的官方下载网址 https://www.getpostman.com/downloads/

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240223200228.png)

PostMan 界面的组成部分，从上到下，从左到右，分别是：
- 菜单栏
- 工具栏
- 左侧历史记录与集合面板
- 请求页签
- 请求地址区域
- 请求参数区域
- 响应结果区域
- 状态栏

### 使用 PostMan 测试 GET 接口

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240223201241.png)

1. 选择请求的方式
2. 填写请求的 URL 地址
3. 填写请求的参数
4. 点击 Send 按钮发起 GET 请求
5. 查看服务器响应的结果

### 使用 PostMan 测试 POST 接口

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240223201200.png)

1. 选择请求的方式
2. 填写请求的 URL 地址
3. 选择 Body 面板并勾选数据格式
4. 填写要发送到服务器的数据
5. 点击 Send 按钮发起 POST 请求
6. 查看服务器响应的结果

### 接口文档

接口文档，顾名思义就是接口的说明文档，它是我们调用接口的依据。好的接口文档包含了对接口 URL，参数以及输出内容的说明，我们参照接口文档就能方便的知道接口的作用，以及接口如何进行调用。

接口文档组成：
接口文档可以包含很多信息，也可以按需进行精简，不过，一个合格的接口文档，应该包含以下 6 项内容，从而为接口的调用提供依据：
- 接口名称：用来标识各个接口的简单说明，如登录接口，获取图书列表接口等。
- 接口 URL：接口的调用地址。
- 调用方式：接口的调用方式，如 GET 或 POST。
- 参数格式：接口需要传递的参数，每个参数必须包含参数名称、参数类型、是否必选、参数说明这 4 项内容。
- 响应格式：接口的返回值的详细描述，一般包含数据名称、数据类型、说明 3 项内容。
- 返回示例（可选）：通过对象的形式，例举服务器返回数据的结构。

## 案例 - 图书管理

用到的库和插件
- 用到的 css 库 bootstrap.css
- 用到的 javascript 库 jquery.js
- 用到的 vs code 插件 Bootstrap 3 Snippets

核心代码段

- 渲染图书列表

```js
function getBookList() {
    // 1. 发起 ajax 请求获取图书列表数据
    $.get('http://www.liulongbin.top:3006/api/getbooks', function(res) {
        // 2. 获取列表数据是否成功
        if (res.status !== 200) return alert('获取图书列表失败！')
        // 3. 渲染页面结构
        var rows = []
        $.each(res.data, function(i, item) { // 4. 循环拼接字符串
            rows.push('<tr><td>' + item.id + '</td><td>' + item.bookname + '</td><td>' + item.author + '</td><td>' + item.publisher + '</td><td><a href="javascript:;">删除</a></td></tr>')
        })
        $('#bookBody').empty().append(rows.join('')) // 5. 渲染表格结构
    })
}
```

- 删除图书

```js
// 1. 为按钮绑定点击事件处理函数
$('tbody').on('click', '.del', function() {
    // 2. 获取要删除的图书的 Id
    var id = $(this).attr('data-id')
    $.ajax({ // 3. 发起 ajax 请求，根据 id 删除对应的图书
        type: 'GET',
        url: 'http://www.liulongbin.top:3006/api/delbook',
        data: { id: id },
        success: function(res) {
            if (res.status !== 200) return alert('删除图书失败！') 
            getBookList() // 4. 删除成功后，重新加载图书列表
        }
    })
})
```

- 删除图书

```js
// 1. 检测内容是否为空
var bookname = $('#bookname').val()
var author = $('#author').val()
var publisher = $('#publisher').val()
if (bookname === '' || author === '' || publisher === '') {
    return alert('请完整填写图书信息！')
}
// 2. 发起 ajax 请求，添加图书信息
$.post(
    'http://www.liulongbin.top:3006/api/addbook',
    { bookname: bookname, author: author, publisher: publisher },
    function(res) {
        // 3. 判断是否添加成功
        if (res.status !== 201) return alert('添加图书失败！')
        getBookList() // 4. 添加成功后，刷新图书列表
        $('input:text').val('') // 5. 清空文本框内容
    }
)
```

## 案例 – 聊天机器人

![image.png|300](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240223202149.png)

实现步骤：
1. 梳理案例的代码结构
2. 将用户输入的内容渲染到聊天窗口
3. 发起请求获取聊天消息
4. 将机器人的聊天内容转为语音
5. 通过 `<audio>` 播放语音
6. 使用回车键发送消息

梳理案例的代码结构
- 梳理页面的 UI 布局
- 将业务代码抽离到 chat.js 中
- 了解 resetui() 函数的作用

核心代码段

将用户输入的内容渲染到聊天窗口

```js
// 为发送按钮绑定点击事件处理函数
$('#btnSend').on('click', function () {
    var text = $('#ipt').val().trim() // 获取用户输入的内容
    if (text.length <= 0) { // 判断用户输入的内容是否为空
       return $('#ipt').val('')
    }
    // 将用户输入的内容显示到聊天窗口中
    $('#talk_list').append('<li class="right_word"><img src="img/person02.png" /> <span>' + text + '</span></li>')
    resetui() // 重置滚动条的位置
    $(‘#ipt’).val('') // 清空输入框的内容

    // TODO: 发起请求，获取聊天消息
})
```

发起请求获取聊天消息

```js
function getMsg(text) {
    $.ajax({
      method: 'GET',
      url: 'http://ajax.frontend.itheima.net:3006/api/robot',
      data: {
        spoken: text
      },
      success: function (res) {
        if (res.message === 'success') {
            var msg = res.data.info.text
            $('#talk_list').append('<li class="left_word"><img src="img/person01.png" /> <span>' + msg + '</span></li>')
            resetui()
            // TODO: 发起请求，将机器人的聊天消息转为语音格式
        }
      }
    })
}
```

将机器人的聊天内容转为语音

```js
  function getVoice(text) {
    $.ajax({
      method: 'GET',
      url: 'http://ajax.frontend.itheima.net:3006/api/synthesize',
      data: {
        text: text
      },
      success: function (res) {
        // 如果请求成功，则 res.voiceUrl 是服务器返回的音频 URL 地址
        if (res.status === 200) {
            $('#voice').attr('src', res.voiceUrl)
        }
      }
    })
  }
```

通过 `<audio>` 播放语音

```js
<!-- 音频播放语音内容 -->
<audio src="" id="voice" autoplay style="display: none;"></audio>
```

使用回车发送消息

```js
// 让文本输入框响应回车事件后，提交消息
$('#ipt').on('keyup', function (e) {
    // e.keyCode 可以获取到当前按键的编码
    if (e.keyCode === 13) {
        // 调用按钮元素的 click 函数，可以通过编程的形式触发按钮的点击事件
        $('#btnSend').click()
    }
})
```
