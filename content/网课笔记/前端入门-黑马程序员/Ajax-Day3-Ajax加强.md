---
date created: 2024-03-10T10:58:15+08:00
date modified: 2024-03-10T11:05:00+08:00
---

## 1. XMLHttpRequest 的基本使用

### 1.1 什么是 XMLHttpRequest

XMLHttpRequest（简称 xhr）是浏览器提供的 Javascript 对象，通过它，可以请求服务器上的数据资源。之前所学的 jQuery 中的 Ajax 函数，就是基于 xhr 对象封装出来的。

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240310105956.png)

### 1.2 使用 xhr 发起 GET 请求

```js
// 1. 创建 XHR 对象
var xhr = new XMLHttpRequest()
// 2. 调用 open 函数，指定 请求方式 与 URL地址
xhr.open('GET', 'http://www.liulongbin.top:3006/api/getbooks')
// 3. 调用 send 函数，发起 Ajax 请求
xhr.send()
// 4. 监听 onreadystatechange 事件
xhr.onreadystatechange = function() {
    // 4.1 监听 xhr 对象的请求状态 readyState ；与服务器响应的状态 status
    if (xhr.readyState === 4 && xhr.status === 200) {
        // 4.2 打印服务器响应回来的数据
        console.log(xhr.responseText)
    }
}
```

### 1.3 xhr 对象的 readyState 属性

XMLHttpRequest 对象的 readyState 属性，用来表示当前 Ajax 请求所处的状态。每个 Ajax 请求必然处于以下状态中的一个：

| 值   | 状态               | 描述                                  |
| --- | ---------------- | ----------------------------------- |
| 0   | UNSENT           | XMLHttpRequest 对象已被创建，但尚未调用 open 方法。 |
| 1   | OPENED           | open() 方法已经被调用。                     |
| 2   | HEADERS_RECEIVED | send() 方法已经被调用，响应头也已经被接收。           |
| 3   | LOADING          | 数据接收中，此时 response 属性中已经包含部分数据。      |
| 4   | DONE             | Ajax 请求完成，这意味着数据传输已经彻底完成或失败。        |

### 1.4 使用xhr发起带参数的GET请求

使用 xhr 对象发起带参数的 GET 请求时，只需在调用 xhr.open 期间，为 URL 地址指定参数即可：

```js
// ...省略不必要的代码
xhr.open('GET', 'http://www.liulongbin.top:3006/api/getbooks?id=1')
// ...省略不必要的代码

```

这种在 URL 地址后面拼接的参数，叫做**查询字符串**。

### 1.5 查询字符串

定义：查询字符串（URL 参数）是指在 URL 的末尾加上用于向服务器发送信息的字符串（变量）。
格式：将英文的 `?` 放在URL 的末尾，然后再加上 `参数＝值` ，想加上多个参数的话，使用 `&` 符号进行分隔。以这个形式，可以将想要发送给服务器的数据添加到 URL 中。

```js
// 不带参数的 URL 地址
http://www.liulongbin.top:3006/api/getbooks
// 带一个参数的 URL 地址
http://www.liulongbin.top:3006/api/getbooks?id=1
// 带两个参数的 URL 地址
http://www.liulongbin.top:3006/api/getbooks?id=1&bookname=西游记

```

GET请求携带参数的本质
无论使用 `$.ajax()`，还是使用 `$.get()`，又或者直接使用 xhr 对象发起 GET 请求，当需要携带参数的时候，本质上，都是直接将参数以查询字符串的形式，追加到 URL 地址的后面，发送到服务器的。

```js
$.get('url', {name: 'zs', age: 20}, function() {})
// 等价于
$.get('url?name=zs&age=20', function() {})

$.ajax({ method: 'GET', url: 'url', data: {name: 'zs', age: 20}, success: function() {} })
// 等价于
$.ajax({ method: 'GET', url: 'url?name=zs&age=20', success: function() {} })

```

### 1.6 URL编码与解码

URL 地址中，只允许出现英文相关的字母、标点符号、数字，因此，在 URL 地址中不允许出现中文字符。
如果 URL 中需要包含中文这样的字符，则必须对中文字符进行编码（转义）。
URL编码的原则：使用安全的字符（没有特殊用途或者特殊意义的可打印字符）去表示那些不安全的字符。
URL编码原则的通俗理解：使用英文字符去表示非英文字符。

```js
http://www.liulongbin.top:3006/api/getbooks?id=1&bookname=西游记
// 经过 URL 编码之后，URL地址变成了如下格式：
http://www.liulongbin.top:3006/api/getbooks?id=1&bookname=%E8%A5%BF%E6%B8%B8%E8%AE%B0

```

浏览器提供了 URL 编码与解码的 API，分别是：

```js
encodeURI('黑马程序员')
// 输出字符串  %E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98
decodeURI('%E9%BB%91%E9%A9%AC')
// 输出字符串  黑马

```

由于浏览器会自动对 URL 地址进行编码操作，因此，大多数情况下，程序员不需要关心 URL 地址的编码与解码操作。[点击此处](https://blog.csdn.net/Lxd_0111/article/details/78028889)了解更多关于URL编码知识

### 1.7 使用xhr发起POST请求

```js
// 1. 创建 xhr 对象
var xhr = new XMLHttpRequest()
// 2. 调用 open()
xhr.open('POST', 'http://www.liulongbin.top:3006/api/addbook')
// 3. 设置 Content-Type 属性（固定写法）
xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded')
// 4. 调用 send()，同时将数据以查询字符串的形式，提交给服务器
xhr.send('bookname=水浒传&author=施耐庵&publisher=天津图书出版社')
// 5. 监听 onreadystatechange 事件
xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 200) {
        console.log(xhr.responseText)
    }
}

```

## 数据交换格式

### 2.1 什么是数据交换格式

数据交换格式，就是服务器端与客户端之间进行数据传输与交换的格式。
前端领域，经常提及的两种数据交换格式分别是 XML 和 JSON。其中 XML 用的非常少，所以，我们重点要学习的数据交换格式就是 JSON。

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240310111633.png)

### 2.2 可扩展标记语言 XML

XML 的英文全称是 EXtensible Markup Language，即可扩展标记语言。因此，XML 和 HTML 类似，也是一种标记语言。

XML 和 HTML 虽然都是标记语言，但是，它们两者之间没有任何的关系。
- HTML 被设计用来描述网页上的内容，是网页内容的载体
- XML 被设计用来传输和存储数据，是数据的载体

缺点：
- XML 格式臃肿，和数据无关的代码多，体积大，传输效率低；
- 在 Javascript 中解析 XML 比较麻烦

### 2.3 JavaScript 对象表示法 JSON

#### 2.3.1 JSON 概念

概念：JSON 的英文全称是 JavaScript Object Notation，即“JavaScript 对象表示法”。简单来讲，JSON 就是 Javascript 对象和数组的字符串表示法，它使用文本表示一个 JS 对象或数组的信息，因此，JSON 的本质是字符串。

作用：JSON 是一种轻量级的文本数据交换格式，在作用上类似于 XML，专门用于存储和传输数据，但是 JSON 比 XML 更小、更快、更易解析。

现状：JSON 是在 2001 年开始被推广和使用的数据格式，到现今为止，JSON 已经成为了主流的数据交换格式。

#### 2.3.2 JSON的两种结构

JSON 就是用字符串来表示 Javascript 的对象和数组。所以，JSON 中包含**对象**和**数组**两种结构，通过这两种结构的相互嵌套，可以表示各种复杂的数据结构。

**对象结构**：对象结构在 JSON 中表示为 `{ }` 括起来的内容。数据结构为 `{ key: value, key: value, … }` 的键值对结构。其中，key 必须是使用**英文的双引号**包裹的字符串，value 的数据类型可以是**数字、字符串、布尔值、null、数组、对象**6种类型。

数组结构：数组结构在 JSON 中表示为 `[ ]` 括起来的内容。数据结构为 `[ "java", "javascript", 30, true … ]` 。数组中数据的类型可以是**数字、字符串、布尔值、null、数组、对象**6种类型。

#### 2.3.3 JSON 语法注意事项

1. 属性名必须使用双引号包裹
2. 字符串类型的值必须使用双引号包裹
3. JSON 中不允许使用单引号表示字符串
4. JSON 中不能写注释
5. JSON 的最外层必须是对象或数组格式
6. 不能使用 undefined 或函数作为 JSON 的值

JSON 的作用：在计算机与网络之间存储和传输数据。
JSON 的本质：用字符串来表示 Javascript 对象数据或数组数据

#### 2.3.4 JSON和JS对象的关系

JSON 是 JS 对象的字符串表示法，它使用文本表示一个 JS 对象的信息，本质是一个字符串。例如：
```js
//这是一个对象
var obj = {a: 'Hello', b: 'World'}

//这是一个 JSON 字符串，本质是一个字符串
var json = '{"a": "Hello", "b": "World"}' 

```

#### 2.3.5 JSON和JS对象的互转

要实现从 JSON 字符串转换为 JS 对象，使用 JSON.parse() 方法：

```js
var obj = JSON.parse('{"a": "Hello", "b": "World"}')
//结果是 {a: 'Hello', b: 'World'}
```

要实现从 JS 对象转换为 JSON 字符串，使用 JSON.stringify() 方法：

```js
var json = JSON.stringify({a: 'Hello', b: 'World'})
//结果是 '{"a": "Hello", "b": "World"}'
```

## 封装自己的 Ajax 函数

## XMLHttpRequest Level2 的新特性

## jQuery 高级用法

## axios