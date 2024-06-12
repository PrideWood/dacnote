#### 25 配合在线数据库，搭建个人管理后台

应用场景：背单词，阅读文章、论文记录、产品销售成交记录
我自己比如：在更新视频号时记录更新的日期、表达本身、出自的剧名、集数等
举例：微习惯记录
方法：通过 iframe 代码将在线表格网页嵌入 OB 页面即可
Johnny 展示的在线数据库，~~排除 hipacloud（要付费）~~
- 多维表格
- 维格表
- Seatable
- Airtable（服务器在国外，加载慢，不会实时更新）
- 语雀数据表（提交后需要重新打开才能再次填写，不会实时更新）

#### 39 利用 OB 的 URI 协议，添加或更新 Airtable 中的数据到 OB

插件：Advanced Obsidian URI
目标效果：在 Airtable 里写内容也会实时更新到 OB 中
本集内容主要涉及 Airtable 内的数据处理，暂不深究。
![Pasted image 20240113152742](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/Pasted%20image%2020240113152742.png)
公式也不用看懂，先用其功能，之后我整理一下 Johnny 学 Airtable 的笔记，看看有没有讲
必须用到的公式（对整个 URI 中内容进行编码）

```
ENCODE_URL_COMPONENT()
```

#### 55 用 Vika 实现 Obsidian 中笔记的智能管理

效果：同时给多条笔记添加属性并能够通过点击 Vika 里的 URI 回到 OB 对应笔记；同时利用 Vika 自身的数据分析功能，查看看板、日历视图等。
插件：Templater
实现步骤：
1. 注册 Vika 账户，创建维格表，前三列设置为 ID, Title, OBURI，其余自定义
2. 找到 API 并添加到对应信息到 Templater 模板的页面中
模板代码需要联系 Johnny 获取，由于本人暂无该需求，所以有需要的同学自行联系。

#### 56 一步步去设置 Vika 和 Airtable 同 Obsidian 的数据同步

注意拿到对应的数据就行了

#### 58 用 Vika 同步管理 Obsidian 中的笔记关键信息升级篇

接 55 集 只是加上了 Tags, Aliases, CreatedTime, UpdatedTime 等字段
多个别名在 frontmatter 里的写法，在 aliases 后写个列表

```
---
aliases:
- 别名1
- 别名2
---
```

#### 59 Obsidian 同 Vika 联动支持自定义同步字段

只需要在设置的模板页面添加自定义的属性名（字段名）
Vika 里的架构图，新建笔记链接到 Obsidian 需要一点 URI 相关的知识

#### 60 一个同步 Vika 和 Airtable 的脚本对近期学习 OB 的综合应用

评论区
> obsidian 与 vika 同步教程（补充教程） https://kdl54sw2h1.feishu.cn/docs/doccnCQzmsmklQUTnTwjoJ5kLqg *@羽飞 yufei*

#### 圣诞礼物 Vika 和 Airtable 到 Obsidian 的同步使用文档及脚本

https://milinshushe.feishu.cn/docs/doccnSwkXMw7tEQJwmBg72yzpLb
