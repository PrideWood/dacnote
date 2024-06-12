---
date created: 2024-01-24T21:03:39+08:00
date modified: 2024-02-07T08:47:26+08:00
---
**学习目标**

- 能够书写表格
- 能够写出无序列表
- 能够写出 4 个常用 input 表单类型
- 能够写出下拉列单
- 能够使用表单元素实现注册页面
- 能够独立查阅 W3C 文档

## 表格

作用：展示数据

**表格标签**

基本语法

```html
<table>
	<tr> //表格中的行
		<th>这是表头</th> // 其中的文本会居中加粗显示
		<td>单元格内的文字</td>  // 单元格
		... 
	</tr> 
	... 
</table>
```

表格属性（写到表格标签中去，不推荐，建议写 CSS 中）

![表格属性.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/%E8%A1%A8%E6%A0%BC%E5%B1%9E%E6%80%A7.png)

**表格结构标签**
表格结构标签：分别用 `<thead>` 标签 表格的头部区域、`<tbody>` 标签 表格的主体区域

**合并单元格**
**跨行合并**：`rowspan="合并单元格的个数"` 最上侧单元格为目标单元格, 写合并代码
**跨列合并**：`colspan="合并单元格的个数"` 最左侧单元格为目标单元格, 写合并代码
步骤：
1. 先确定是跨行还是跨列合并。
2. 找到目标单元格. 写上合并方式 = 合并的单元格数量。比如：`<td colspan="2"></td>`。
3. 删除多余的单元格。

## 列表

作用：用来布局
分类：无序列表、有序列表和自定义列表

无序列表

```html
  <ul> 
       <li>列表项1</li>   
       <li>列表项2</li>   
       <li>列表项3</li>  
   </ul>
```

 1. `<ul></ul>` 中只能嵌套 `<li></li>`，直接在 `<ul></ul>` 标签中输入其他标签或者文字的做法是不被允许的。
 2. `<li>` 与 `</li>` 之间相当于一个容器，可以容纳所有元素
 3. 无序列表会带有自己的样式属性，但在实际使用时，我们会使用 CSS 来设置

有序列表

```html
<ol>   
	<li>列表项1</li>   
	<li>列表项2</li>   
	<li>列表项3</li>   
	... 
</ol>
```

自定义列表：常用于对术语或名词进行解释和描述，定义列表的列表项前没有任何项目符号。

```html
<dl>   
	<dt>名词1</dt>   
	<dd>名词1解释1</dd>   
	<dd>名词1解释2</dd> 
</dl>
```

小结
![列表总结.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/%E5%88%97%E8%A1%A8%E6%80%BB%E7%BB%93.png)

## 表单

在 HTML 标签中， `<form>` 标签用于定义表单域，以实现用户信息的收集和传递。

表单的组成： 在 HTML 中，一个完整的表单通常由表单域、表单控件（也称为表单元素）和 提示信息 3 个部分构成。

### 表单域

```html
<form action="url地址" method="提交方式" name="表单域名称">
	各种表单元素控件
</form>
```

表单常用属性
![表单常用属性.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/%E8%A1%A8%E5%8D%95%E5%B8%B8%E7%94%A8%E5%B1%9E%E6%80%A7.png)

### 表单控件（表单元素）

**`<input>` 表单元素**

```html
<input type="属性值" />
```

type 属性的属性值及其描述如下：
![表单标签.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/%E8%A1%A8%E5%8D%95%E6%A0%87%E7%AD%BE.png)

其他常用属性如下：
![表单其他属性.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/%E8%A1%A8%E5%8D%95%E5%85%B6%E4%BB%96%E5%B1%9E%E6%80%A7.png)
要求单选按钮和复选框有相同的 name 值：只有添加同一个 name 属性，单选按钮才能实现多选一

**`<label>` 标签**：用于绑定一个表单元素, 当点击 `<label>` 标签内的文本时，浏览器就会自动将焦点 (光标) 转到或者选择对应的表单元素上,用来增加用户体验.

```html
<label for="sex">男</label> 
<input type="radio" name="sex" id="sex" />
```

核心： `<label>` 标签的 for 属性应当与相关元素的 id 属性相同。

`<select>` 表单元素

```html
<select>
   <option>选项1</option>
   <option>选项2</option>
   <option>选项3</option>
   ...
 </select>
```

`<textarea>` 表单元素：用于定义多行文本输入的控件（实际开发中不会使用，都是用 CSS 来改变大小）

```html
<textarea rows="3" cols="20"> 文本内容 </textarea>
```

三个名字非常相似的标签：
- 表单域 form：提交区域内表单元素给后台服务器
- 文件域 file 是 input type 属性值
- 上传文件文本域 textarea：可以输入多行文字, 比如留言板 网站介绍等

当前阶段不需要提交表单元素,所以我们只负责表单元素的外观形态即可.

查阅文档： 
W3C : [http://www.w3school.com.cn/](http://www.w3school.com.cn/) 
MDN: [https://developer.mozilla.org/zh-CN/](https://developer.mozilla.org/zh-CN/)

[综合案例-注册页面](C:\Users\24742\Desktop\practice\HTML\HTML基础-Day2-注册页面.html)
