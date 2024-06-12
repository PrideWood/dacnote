#### 57 思维导图

提了一下 Heptabase
OB 和思维导图工具（Xmind，Scapple，ithoughtsx）结合 联动
要点：建立名称唯一的文件，给它添加别名
ithoughtsx 支持分享节点的 URI 以至于可以同 OB 之间进行双向跳转
注意：一定打开 Templater 里的 Trigger Templater on new file creation
模板代码示例

```
---
tags: ithoughts
aliases:
	- <% tp.file.cursor(1) %>
---

# <% tp.file.cursor(2) %>
```

还需借助工具：espanso 开源、免费、跨平台 //这里还没懂
评论区
> 小小提醒下，UP 主视频中显示的 ob 插件除了 templater 外，还要再装个 advanced uri 插件 *@舔蜜的熊*