# 银河系无服务器指南- #1 -简介

> 原文：<https://dev.to/collabcode/o-guia-dos-serverless-das-galaxias-introducao-16e3>

[![Serverless Capa](img/aea50b547023d8384ed723950e378309.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--fvC-CjuG--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://i.ibb.co/c8N8sTg/serverless-capa.jpg)

经过数十年的服务器/基础架构维护，使我们的应用程序保持活动状态，我们能够在容器中开发和部署几乎所有需要的东西。一段时间后，一个新的计算模型出现了，吸引了崇拜者和怀疑论者。

在我看来，这种模式不是用来杀死任何现有的模式，而是用来增加价值。所以我再一次要求你停止寻找不存在的神奇的解决方案，并让你的选择更加理性。

我之所以这么说，是因为最近很多人都把无服务器作为云计算发展的巅峰来销售，但它是否适合您？

我不是来给你这个答案的，但我希望直到这篇文章的结尾**你才能回答**。

## O que é Serverless？

就像其他人在使用无线网络时不关心互联网电缆的位置一样，在无服务器体系结构中，我们不关心服务器的位置，但这并不意味着它们不存在。

基本上，我们不再需要担心我们的代码将如何运行，这样您就可以自由地思考代码将在何处(区域)以及何时运行，甚至在我们的解决方案中是否需要运行代码。

有时我们甚至不需要编写代码，只要让服务部门通信即可。

将应用程序/平台定义为无服务器有四个主要特征:

### 零管理

虽然虚拟机和容器等平台仍需要服务器配置和管理，但服务器无处不在是一种完全不同的体验。当您准备好部署代码时，无需在部署之前预配任何内容或在部署之后管理任何内容。

您必须管理服务器、虚拟机或容器，这不仅需要计算成本，而且还需要包括员工人数、工具、培训、时间、能源、水、电力、运输等。

这些是我们开发人员通常看不到的成本，但他们在那里。通过在云中运行所有内容，并由供应商为我们管理实例或操作系统，此模型极大地改变了应用程序的成本计算。

这里不再适用□的概念，也不需要规则随着计算资源的减少，在高峰时段之后自动进行扩展，因此永远不会出现空闲容量。

### 使用(或不使用@)时支付。@)

这通常鼓励大家第一次体验无服务器模式。完全利用资源而不花一分钱空闲时间是很吸引人的。也就是说，不按闲置的虚拟机或容器实例收费，因此只有在代码执行时才会收费。

对于数据库而言，读/写不需要成本，只需计算运行时间和传输的数据量。

当然，这不包括其他成本，如运行状况监视或其他功能、功能、资源池等的存储成本。

对我来说，当您隐藏体系结构中的成本时，因为当您只专注于这一点时，我们就会忽略一些非常重要的问题，这些问题可能会使我们的服务器解决方案比今天使用的解决方案更昂贵。

我们按日/周/月/年划分的服务利用率指标是什么？我们的用例是 realtime 还是我们的处理时间太长？我们需要多少内存？我的供应商是什么？他对竞争对手收费多少？我的运行时是使用虚拟机并且需要大量内存才能运行的工具，还是使用不太常用的语言？

使用无服务器时，必须考虑所有这些问题。

### 我们可以作为部署单位发挥作用

此体系结构由非常小的、独立的和松散耦合的代码组成(还记得微服务吗？页:1。这样做的主要优点是，我们有部分应用程序是按照您的职责组织的。它们可以独立开发和部署。这样可以减少阻塞，提高开发人员的自主性和工作效率。

我们必须记住的另一个重要问题是我们的功能的大小，它们不一定太小，例如，今天 AWS 支持高达 250 兆字节的舔舔。

我通常使用 API 端点作为部署单元。

### 事件驱动

从长远来看，无服务器的这一方面非常重要。默认情况下，函数没有机器状态，并且在某些事件触发它们之前处于非活动状态。事件是使角色具有生命并提供数据/上下文以便角色执行其工作的原因。

以事件为导向的体系结构并不新鲜，但无服务器计算模型的兴起重新激发了人们对该主题的兴趣，因为默认情况下，所有功能都是以事件为导向的。

如果您想进一步了解面向事件的应用程序是如何工作的，我建议您阅读 Paula Santana 的“系统开发和基于事件的体系结构”一文。

* * *

## 完成…

如果你喜欢这个帖子，不要忘了给喜欢和分享

如果你想知道我在做什么，或者想问什么，请随时到社交网站来找我，比如@[【malakasdev】](https://twitter.com/malaquiasdev)。

为了多读我的帖子访问[【马拉喀什 DEV |生命，代码等】](http://malaquias.dev)。