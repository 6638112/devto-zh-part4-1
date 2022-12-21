# 在 Azure 上创建并测试一个 JavaScript Node.js 无服务器函数

> 原文：<https://dev.to/azure/create-and-test-a-javascript-node-js-serverless-function-on-azure-2d3>

> 本文是 [#ServerlessSeptember](https://dev.to/azure/serverless-september-content-collection-2fhb) 的一部分。在这个无服务器的内容集合中，您可以找到其他有用的文章、详细的教程和视频。9 月份，每天都有来自社区成员和云倡导者的新文章发布，没错，每天都有。
> 
> 在[https://docs.microsoft.com/azure/azure-functions/](https://docs.microsoft.com/azure/azure-functions/?WT.mc_id=devto-blog-jeliknes)了解更多关于微软 Azure 如何实现你的无服务器功能。

Azure Functions 应用程序充当无服务器功能的主机。它是一个部署和扩展单元，定义应用程序的功能，如语言和运行时、安全设置和根 URL 端点。

# 创建一个 Azure 功能应用程序

这个视频是为任何不熟悉 Azure 函数的人设计的，即使你不是从 AWS Lambda 迁移过来的。它介绍了如何创建主机，使用 JavaScript 和 Node.js 编写简单的代码，并从浏览器和命令行测试该功能。

[https://www.youtube.com/embed/YgcUqPzk63c](https://www.youtube.com/embed/YgcUqPzk63c)

您可以查看示例应用程序的源代码，并在“AWS migration”GitHub 存储库中单击一下，将迁移的代码直接部署到 Azure。

## ![GitHub logo](img/a73f630113876d78cff79f59c2125b24.png) [耶路撒冷](https://github.com/JeremyLikness) / [移民](https://github.com/JeremyLikness/AWSMigration)

### 从 AWS Lambda 迁移到 Azure 函数

<article class="markdown-body entry-content container-lg" itemprop="text">

# 将 AWS Lambda 移至 Azure 函数

这是“从 Lambda 迁移到 Azure 函数”视频系列的源代码，演示了如何从 AWS Lambda 迁移到 Azure 函数。

<g-emoji class="g-emoji" alias="cinema" fallback-src="https://github.githubassets.cimg/icons/emoji/unicode/1f3a6.png">🎦</g-emoji> [观看视频系列](https://www.youtube.com/playlist?list=PL1VfiVM16kp8U5E7U2tfJdskXJg8DPPKL) (YouTube 播放列表)

## 快速启动

[![Free Azure Account](img/d9a3cf269ef7f44a874d4d23a7716180.png)](https://jlik.me/gmj) 获得你的[免费 Azure 账户](https://jlik.me/gmj)

您可以快速开始使用迁移的功能。只需点击“部署到 Azure”按钮。请确保输入唯一的前缀(例如，使用您的姓名首字母或添加一个序列)。部署完成后，您可以访问和测试该功能。

[![Deploy to Azure](img/c520bd44b91f9a1d115e1745f2ff9dea.png)](https://azuredeploy.net/)

> 要启用缓存，请在创建后导航到存储帐户。点击`Table service`下的`Tables`，然后添加一个名为`primes`的表格。

## 代码

这个存储库包含所有相关项目的代码。

### 源(“纯”)函数

函数本身决定了传递的数是否是质数。纯功能在`src\isItAPrime.js`中可用…

</article>

[View on GitHub](https://github.com/JeremyLikness/AWSMigration)

在下一篇文章中，我们将探索如何从我们的 AWS Lambda 函数中集成[质数代码](https://github.com/JeremyLikness/AWSMigration/blob/master/azure/portal/isItAPrime/index.js)，包括使用 [Azure 表存储](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview?WT.mc_id=devto-blog-jeliknes)设置缓存。

## 资源

1.  [创建您的免费 Azure 帐户](https://azure.com/free?WT.mc_id=devto-blog-jeliknes)
2.  【Azure 函数的 JavaScript 开发者参考
3.  [如何从 Node.js 使用 Azure 表存储](https://docs.microsoft.com/azure/cosmos-db/table-storage-how-to-use-nodejs?WT.mc_id=devto-blog-jeliknes)