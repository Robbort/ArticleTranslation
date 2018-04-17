# 为什么我的贡献(contribtuins)没有显示在我的个人资料(profile)中？

你的个人资料贡献图是你对GitHub仓库所做贡献的记录。按照协调世界时（UTC）而不是你当地的时区为贡献提供时间戳。只有在满足特定标准的情况下才会计算贡献。在某些情况下，我们可能需要重建你的图表才能显示贡献。

## 被计算了的贡献

### 问题和拉取请求

如果在独立仓库中打开它们，而不是分叉（fork），则问题和拉取请求将出现在你的贡献图上。

### 提交（Commits）

如果满足以下所有条件，提交将显示在你的贡献图上：

- 用于提交的电子邮件地址与你的GitHub帐户关联。
- 提交是在一个独立的仓库中完成的，而不是一个分支，【亲测，只有提交在master分支有效】。
- 提交只有在一下条件下提交才有用:
- 在默认的分支上(通常是 `master`)
- 在`gh-pages`分支上 (对于仓库中包含的[Project Pages 站点](https://help.github.com/articles/user-organization-and-project-pages/#project-pages-sites))

另外，至少一项的一项必须要有：

- 你是仓库上的协作者，或者是拥有仓库的组织的成员。
- 你已分叉(fork)仓库。
- 你已在仓库中打开拉取请求或问题。
- 你已经为仓库加星标。

## 不计入贡献的常见原因

- 要显示在你的个人资料贡献图上，合作的提交必须满足与一位作者相同标准的提交。
- 当拉取请求被合并且提交被压缩时，只有合并拉取请求的用户和打开拉取请求的用户[记录贡献](https://help.github.com/articles/viewing-contributions-on-your-profile/). 没有其他提供者会记录贡献。
- 当重新提交提交时，提交的原始作者和重新提交的提交者（无论是在命令行还是在GitHub上）都会收到贡献记录。

### 不到24小时前提交

在提交满足要求的提交以作为贡献之后，你可能需要等待长达24小时才能看到贡献出现在你的贡献图上。

### 你尚未将你的本地Git提交电子邮件添加到你的个人资料

必须使用已添加到GitHub配置文件中的电子邮件地址进行提交，才能显示在你的贡献图上。 你可以通过在提交URL的末尾添加`.patch`来检查用于提交的电子邮件地址，例如， [https://github.com/octocat/octocat.github.io/commit/67c0afc1da354d8571f51b6f0af8f2794117fd10.patch](https://github.com/octocat/octocat.github.io/commit/67c0afc1da354d8571f51b6f0af8f2794117fd10.patch):

```
From 67c0afc1da354d8571f51b6f0af8f2794117fd10 Mon Sep 17 00:00:00 2001
From: The Octocat (octocat@nowhere.com)
Date: Sun, 27 Apr 2014 15:36:39 +0530
Subject: [PATCH] updated index for better welcome message
```

在`From:`后面的邮箱地址就是[本地git配置](https://help.github.com/articles/set-up-git/).在这个例子中，用来提交的邮箱地址是`octocat@nowhere.com`.

假如被用来提交的邮箱地址没有被加入到你的GitHub个人资料中，你须要[添加电子邮箱地址](https://help.github.com/articles/adding-an-email-address-to-your-github-account/)到你的GitHub账号。当你添加了新的邮箱地址，你的贡献图才会自动重新创建。

	通用电子邮件地址 - 例如`jane @ computer.local` - 不能添加到GitHub帐户。 如果你使用此类电子邮件进行提交，提交将不会链接到你的GitHub配置文件，并且不会显示在你的贡献图中。

### 提交并未在默认或`gh-pages`分支中进行

只有在默认分支（通常为`master`）或`gh-pages`分支（对于具有[Project Pages站点的仓库](https://help.github.com/articles/user-organization-and-project-pages/#project-pages-sites)）中进行提交时，才会对提交进行计数。 如果你的提交属于非默认或非`gh-pages`分支，并且你希望它们计入你的贡献，则需要执行以下操作之一：

> [打开拉取请求](https://help.github.com/articles/creating-a-pull-request/)，将你的更改合并到默认分支或`gh-pages`分支中。
> [更改仓库的默认分支](https://help.github.com/articles/setting-the-default-branch/)。

更改仓库的默认分支将更改所有仓库协作者的分支。 只有在你希望新分支成为未来所有请求和提交所针对的基础时才执行此操作。

### 提交合作作者无权访问仓库

如果在共享作者无权访问的仓库中进行提交，则该提交不会计入共同作者的贡献。

### 提交是在一个分支中完成的

在分叉中作出的提交不会计入你的贡献。 要使它们成为数字，你必须执行以下操作之一：

- [打开拉取请求](https://help.github.com/articles/creating-a-pull-request/)以将你的更改合并到父仓库中。
- 要分离fork并将其转换为GitHub上的独立仓库，请联系[GitHub支持](https://github.com/contact)。 如果fork有自己的fork，让支持人员知道fork是否应该随仓库一起移动到新的网络中或保留在当前网络中。 有关更多信息，请参阅“[关于fork(https://help.github.com/articles/about-forks/)]”。

### 提交请求被合并并被压缩

在[合并和压缩](https://help.github.com/articles/about-pull-request-merges/)的拉取请求中进行的提交不会计入你的贡献。 只有合并拉取请求的用户和打开拉取请求的用户才能收到贡献。 没有其他提供者会记录贡献。

	如若此翻译侵权，请联系删除。
PS：GitHub上有很多词，我觉得要是翻译成中文意思就会怪怪的，所以有些我在括号里保留了原来的英文意思。