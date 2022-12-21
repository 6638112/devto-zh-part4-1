# API 列表 2.0 简介

> 原文：<https://dev.to/surfer77/introducing-api-list-2-0-1d7b>

*TL；博士:一个完整的重新设计，一个新的博客，公司网页，收藏，评论和 upvotes，Algolia 搜索和更多。*

2017 年开始是一个电子表格，然后是一个简单的网站。最初，它有大约 100 个由我手动提交的 API，然后人们开始贡献，它成为开发人员寻找用于他们的项目、hackaton 或初创公司的 API 的有用资源。

当时我有许多兼职项目，所以我离开 API 列表去做“自动导航”，只是在新添加的 API 进来时批准它们。

2018 年我注意到该网站在谷歌的排名开始上升，我也注意到越来越多的大学在他们的 CS 课程中引用 API 列表(大多数引用来自大学、github 课程或 udemy 课程)。这是回到 API 列表工作的巨大动力，在一吨小时的工作之后，我很高兴发布 API 列表 2.0，它有许多新特性！

## 堆栈

之前的版本是用 Vue 搭建的，这次我决定用 vanilla JS 做所有的事情，这样我就不需要每次 Vue 更新什么东西的时候都重构了(听说新的 Vue 要出来了)。

堆栈是:

*   快递 JS。
*   客户端上的普通 JS。
*   Turbolinks 让它看起来很时髦。
*   用于造型的 TailwindCSS。
*   数据库的 MongoDB。
*   服务器和图像的数字海洋。

## 重新设计

旧版本的 API 列表使用的是从  预先设计的模板，我甚至没有一个标志😊。

我不是设计师，但在看了大量 Youtube 视频和阅读了 文章(感谢和)后，我对最终结果非常满意(仍然缺少一些功能)。

它实用、简单、有趣，让主 API feed 感觉像一个真实的列表(以前不是)。

我的女朋友为我设计了这个标志，我很喜欢它！。

[![](img/2eff33a0f95187e186baba2e0aff44b8.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--EQLE0y4K--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.amazonaws.com/i/5l9mri3qehg39dtgmjb1.png)

## 使用特定 API 的评论、upvotes 和公司

我在 API 档案中添加了评论、upvotes 和“使用这个 API 的公司”,目的是让这个网站更像一个“社交网络”。有点像产品搜索，希望社区能让最好的 API 脱颖而出。

到目前为止(测试 2 周后)还没有任何评论，但 upvotes 一直运行得很好，我们会随着时间的推移而看到。

## 阿哥利亚搜索

我很高兴把站内搜索搬到阿尔戈利亚。在 API List 1.0 中，我使用的是直接的 Mongodb 查询，但是效果并不好。我花了一天的时间来实现 Algolia，他们的免费计划现在已经足够了，不能推荐他们。

## API 集合

当有人在搜索栏中搜索一个 API 时，我将它保存到数据库中，然后分析它(目前是手动的)，目的是创建“集合”。我在生产中有这个代码，但到目前为止还没有创建许多集合。这里可以看到一个“自由 API”集合，例如 https://apilist.fun/collection/free-apis 的

我想在未来做“公共收藏”，这样每个用户都可以创建自己的收藏。如果你想看这个，请告诉我。

## 公司页面

我想知道更多关于公司和开发者如何使用他们的 API，和/或他们基于什么 API 构建。

新的公司页面以公司为特色，解释他们如何使用 API。把它想象成 API 的独立黑客。我面试的第一家公司是，面试可以看这里:。

如果你的项目/公司提供或者严重依赖 API，请在这里添加你的公司:

## 打开博客

我也用 Ghost 开了这个博客，这是我第一次用 Ghost，我推荐给任何想要一个简单又好看的博客的人。

我不是一个伟大的作家，但长期目标是让其他人在这个博客中自由地写关于 API 的文章。如果你想成为一名贡献者，请。

* * *

## 接下来是什么？

就是这样！目前，这些是我能透露的所有更新。

在接下来的几周，我会修复新发现的错误，并重新设计我认为可以快速发布的东西(咳咳响应细节)。

我希望到 2019 年底，增加至少 400 个新的 API，并让 100 家公司拥有自己的公司页面。

从长远来看，我想组织几个在线黑客。我是一个内向的人，所以组织、拓展等不是我的强项，但这将是一个很好的挑战。