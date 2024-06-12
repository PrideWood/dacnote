4 使用 Templater 在阅读时，一键完成为选中的关键词创建笔记、添加双链、移动到指定文件夹并应用设定模板等一系列操作

插件：Templater
举例：
（代码含义请看原视频）
TP-AddLearnLink 的模板

```
 [[<% (await tp.file.create_new(tp.file.find_tfile("Tp-Learn"),tp.file.selection())).basename %>]]
```

TP-Learn 的模板 # 我的学习内容 这里我会写一些关于学习的内容 

```
<% await tp.file.move("01-Learn/" + tp.file.title) %>
```

在插件设置中设置快捷键，快速触发
注意：该插件设置中 Trigger Templater on new file creation 必须打开

#### 45 插件 Templater 的两个懒人用法

演示代码链接 https://airtable.com/shrqmxUIfUg8Y0ca8
搬过来
代码段 1 更改文件所在文件夹

```
<% await tp.file.move("/目标文件夹/" + ((tp.file.title.includes("未命名") || tp.file.title.toLowerCase().includes("untitled"))  ? (await tp.system.prompt("请输入要创建的文件名")) : tp.file.title)) %>
```

代码 2 给同一文件夹下文件以文件夹名开头命名 如文件夹名为 Johnny，其下方文件分别命名为 Johnny 基本情况、Johnny 案情调查，等等。

```
<% await tp.file.rename(tp.file.path(true).split('/')[tp.file.path(true).split('/').length-2] + " " + ((tp.file.title.includes("未命名") || tp.file.title.toLowerCase().includes("untitled")) ? (await tp.system.prompt("请输入要创建的文件名")) : tp.file.title)) %>
```

#### 47 Templater 一键提取 Annotator 生成的读书笔记，然后用 Note Refactor 将其碎片化

联系 13 集、20 集
模板下载地址，「OB Templater Scripts」 链接： https://www.aliyundrive.com/s/TLSPiG5D95v

#### 48 使用 Templater 配合 Markmind 做思维导图、原子化读书笔记

Markmind 含付费服务（80RMB）
演示代码链接同上节