---
title: What is GitHub?
draft: false
tags:
---
 
## Github - 了解开源相关的概念

### 1. 开源 vs 闭源

|      | 开源                         | 闭源             |
| ---- | -------------------------- | -------------- |
| 概念   | 开源即开放源代码（Open source code） | 软件的代码是封闭的      |
| 基本含义 | 代码是公开的                     | 只有作者能看到闭源软件的代码 |
| 特点   | 任何人都可以去查看，修改和使用开源代码        | 只有作者能对源代码进行修改  |
| 通俗理解 | 不仅提供程序还提供程序的源代码            | 只提供程序，不提供源代码   |

### 2. 什么是开源许可协议

开源并不意味着完全没有限制，为了限制使用者的使用范围和保护作者的权利，每个开源项目都应该遵守开源许可协议（ Open Source License ）。

### 3. 常见的 5 种开源许可协议

1. BSD（Berkeley Software Distribution）
2. Apache Licence 2.0
3. GPL（GNU General Public License）
	- 具有传染性的一种开源协议，不允许修改后和衍生的代码做为闭源的商业软件发布和销售
	- 使用 GPL 的最著名的软件项目是：Linux
4. LGPL（GNU Lesser General Public License）
5. MIT（Massachusetts Institute of Technology, MIT）
	- 是目前限制最少的协议，唯一的条件：在修改后的代码或者发行包中，必须包含原作者的许可信息
	- 使用 MIT 的软件项目有：jquery、Node.js

关于更多开源许可协议的介绍，可以参考 [此处](https://www.runoob.com/w3cnote/open-source-license.html) 了解开源相关的概念

### 4. 为什么要拥抱开源

开源的核心思想是“我为人人，人人为我”，人们越来越喜欢开源大致是出于以下 3 个原因：
1. 开源给使用者更多的控制权
2. 开源让学习变得容易
3. 开源才有真正的安全
开源是软件开发领域的大趋势，拥抱开源就像站在了巨人的肩膀上，不用自己重复造轮子，让开发越来越容易。

### 5. 开源项目托管平台

专门用于免费存放开源项目源代码的网站，叫做开源项目托管平台。目前世界上比较出名的开源项目托管平台
主要有以下 3 个：
- Github（全球最牛的开源项目托管平台，没有之一）
- Gitlab（对代码私有性支持较好，因此企业用户较多）
- Gitee（又叫做码云，是国产的开源项目托管平台。访问速度快、纯中文界面、使用友好）

注意：以上 3 个开源项目托管平台，只能托管以 Git 管理的项目源代码，因此，它们的名字都以 Git 开头。

### 6. 什么是 Github

Github 是全球最大的开源项目托管平台。因为只支持 Git 作为唯一的版本控制工具，故名 GitHub。
在 Github 中，你可以：
1. 关注自己喜欢的开源项目，为其点赞打 call
2. 为自己喜欢的开源项目做贡献（Pull Request）
3. 和开源项目的作者讨论 Bug 和提需求 （Issues）
4. 把喜欢的项目复制一份作为自己的项目进行修改（Fork）
5. 创建属于自己的开源项目
6. etc…

So，Github ≠ Git

## Github - 注册账号（略）

## Github - 远程仓库的使用

### 1. 新建空白远程仓库（略）

### 2. 远程仓库的两种访问方式： HTTPS 和 SSH

- HTTPS：零配置；但是每次访问仓库时，需要重复输入 Github 的账号和密码才能访问成功
- 需要进行额外的配置；但是配置成功后，每次访问仓库时，不需重复输入 Github 的账号和密码（在实际开发中，推荐使用）

#### 1.  基于 HTTPS 将本地仓库上传到 Github

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240611193849.png)

第二次提交仅需运行 `git push` 命令

#### 2. 基于 SSH 将本地仓库上传到 Github

SSH key
- SSH key 的作用：实现本地仓库和 Github 之间免登录的加密数据传输。
- SSH key 的好处：免登录身份认证、数据加密传输。
- SSH key 由两部分组成，分别是：
	1. `id_rsa`（私钥文件，存放于客户端的电脑中即可）
	2. `id_rsa.pub`（公钥文件，需要配置到 Github 中）Github - 远程仓库的使用
- 生成 SSH key
	1. 打开 Git Bash
	2. 粘贴如下的命令
		- `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
	3. 连续敲击 3 次回车，即可在 `C:\Users\用户名文件夹\.ssh` 目录中生成 `id_rsa` 和 `id_rsa.pub` 两个文件

配置 SSH key
1. 使用记事本打开 id_rsa.pub 文件，复制里面的文本内容
2. 在浏览器中登录 Github，点击头像 -> Settings -> SSH and GPG Keys -> New SSH key
3. 将 id_rsa.pub 文件中的内容，粘贴到 Key 对应的文本框中
4. 在 Title 文本框中任意填写一个名称，来标识这个 Key 从何而来
5. 检测 Github 的 SSH key 是否配置成功
	- 打开 Git Bash，输入如下的命令并回车执行：`ssh -T git@github.com`
	- 上述的命令执行成功后，会看提示消息再输入 yes 之后，看到提示“ successfully authenticated”消息，证明 SSH key 已配置成功

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240611200942.png)

### 3. 将远程仓库克隆到本地

打开 Git Bash，输入如下的命令并回车执行：

```bash
git clone 远程仓库的地址
```

## Git 分支 - 本地分支操作

### 1. 分支的概念

分支就是科幻电影里面的平行宇宙，当你正在电脑前努力学习 Git 的时候，另一个你正在另一个平行宇宙里努力学习 SVN。如果两个平行宇宙互不干扰，那对现在的你也没啥影响。不过，在某个时间点，两个平行宇宙合并了，结果，你既学会了 Git 又学会了 SVN！

### 2. 分支在实际开发中的作用

在进行多人协作开发的时候，为了防止互相干扰，提高协同开发的体验，建议每个开发者都基于分支进行项目功能的开发，例如：

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240611203452.png)

### 3. master 主分支

在初始化本地 Git 仓库的时候，Git 默认已经帮我们创建了一个名字叫做 master 的分支。通常我们把这个 master 分支叫做主分支（上图中的黑色线条）。
在实际工作中，master 主分支的作用是：用来保存和记录整个项目已完成的功能代码。
因此，不允许程序员直接在 master 分支上修改代码，因为这样做的风险太高，容易导致整个项目崩溃。

### 4. 功能分支

由于程序员不能直接在 master 分支上进行功能的开发，所以就有了功能分支的概念。
功能分支指的是专门用来开发新功能的分支，它是临时从 master 主分支上分叉出来的，当新功能开发且测试
完毕后，最终需要合并到 master 主分支上。

### 5. 查看分支列表

使用如下的命令，可以查看当前 Git 仓库中所有的分支列表：

```bash
git branch
```

注意：运行的结果分支名字前面的 `*` 号表示当前所处的分支。

### 6. 创建新分支

使用如下的命令，可以基于当前分支，创建一个新的分支，此时，新分支中的代码和当前分支完全一样：

```bash
git branch login
```

图示如下：

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240611204852.png)

### 7. 切换分支

使用如下的命令，可以切换到指定的分支上进行开发：

```bash
git checkout login
```

图示如下：

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240611205025.png)

### 8. 分支的快速创建和切换

使用如下的命令，可以创建指定名称的新分支，并立即切换到新分支上：

```bash
# -b 表示创建一个新分支
# checkout表示切换到新分支上
git checkout -b 分支名称
```

图示如下：

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240611205225.png)

注意：
`git checkout -b 分支名称` 是下面两条命令的简写形式：① `git branch 分支名称`；② `git checkout 分支名称`

### 9. 合并分支

功能分支的代码开发测试完毕之后，可以使用如下的命令，将完成后的代码合并到 master 主分支上：

```bash
# 切换到 master 分支
git checkout master
# 合并功能，将 login 分支代码合并到主分支
git merge login
```

图示如下：

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240611205750.png)

合并分支时的注意点：假设要把 C 分支的代码合并到 A 分支，则必须先切换到 A 分支上，再运行 `git merge` 命令，来合并 C 分支！

### 9. 删除分支

当把功能分支的代码合并到 master 主分支上以后，就可以使用如下的命令，删除对应的功能分支：

```bash
git branch -d 分支名称
```

图示如下：

![image.png](https://pictures-1323793543.cos.ap-nanjing.myqcloud.com/pics/20240611205921.png)

### 10. 遇到冲突时的分支合并

如果在两个不同的分支中，对同一个文件进行了不同的修改，Git 就没法干净的合并它们。 此时，我们需要打开这些包含冲突的文件然后手动解决冲突。

```bash
# 假设:在把 reg 分支合并到 master 分支期间，代码发生了冲突
git checkout master
git merge reg
# 打开包含冲突的文件，手动解决冲突之后，再执行如下的命令
git add .
git commit -m "解决了分支合并冲突的问题"
```

## Git 分支 - 远程分支操作

### 1. 将本地分支推送到远程仓库

如果是**第一次**将本地分支推送到远程仓库，需要运行如下的命令：

```bash
# -u 表示把本地分支和远程分支进行关联，只在第一次推送的时候需要带 -u 参数git push -u 远程仓库的别名 本地分支名称:远程分支名称
# 实际案例:
git push -u origin payment:pay
# 如果希望远程分支的名称和本地分支名称保持一致，可以对命令进行简化:
git push -u origin payment
```

注意：第一次推送分支需要带 `-u` 参数，此后可以直接使用 `git push` 推送代码到远程分支。

### 2. 查看远程仓库中所有的分支列表

通过如下的命令，可以查看远程仓库中，所有的分支列表的信息：

```bash
git remote show 远程仓库名称
```

### 3. 跟踪分支

跟踪分支指的是：从远程仓库中，把远程分支下载到本地仓库中。需要运行的命令如下：

```bash
# 从远程仓库中，把对应的远程分支下载到本地仓库，保持本地分支和远程分支名称相同
git checkout 远程分支的名称
# 示例:
git checkout pay

#从远程仓库中，把对应的远程分支下载到本地仓库，并把下载的本地分支进行重命名
git checkout -b 本地分支名称 远程仓库名称/远程分支名称
# 示例:
git checkout -b payment origin/pay
```

### 4. 拉取远程分支的最新的代码

可以使用如下的命令，把远程分支最新的代码下载到本地对应的分支中：

```bash
git pull
```

### 5. 删除远程分支

可以使用如下的命令，删除远程仓库中指定的分支：

```bash
# 删除远程仓库中，指定名称的远程分支
git push 远程仓库名称 --delete 远程分支名称
# 示例:
git push origin --delete pay
```

## 总结

1. 能够掌握 Git 中基本命令的使用
	- `git init`
	- `git add .`
	- `git commit –m "提交消息"`
	- `git status` 和 `git status -s`
2. 能够使用 Github 创建和维护远程仓库
	- 能够配置 Github 的 SSH 访问
	- 能够将本地仓库上传到 Github
3. 能够掌握 Git 分支的基本使用
	- `git checkout -b 新分支名称`
	- `git push -u origin 新分支名称`
	- `git checkout 分支名称`
	- `git branch`

