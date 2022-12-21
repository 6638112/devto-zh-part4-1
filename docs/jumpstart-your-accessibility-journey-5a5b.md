# 启动您的无障碍之旅

> 原文：<https://dev.to/glitchgirl/jumpstart-your-accessibility-journey-5a5b>

我看到了大量讨论可访问性及其对开发人员的意义的文章，但是我没有看到多少文章讨论如何使您的网站具有可访问性。所以，我想谈谈一些快速提示，可以帮助任何水平的开发人员(和/或设计人员)使他们的项目更容易理解。首先，我将谈论开发者如何测试他们的站点，然后讨论一些我用来使我的站点更好的资源。最后，我将列出一些我认为有用的工具。有时，当人们用一种新的标准来评判网站时，开发者会感到很有压力。我想到的是，当谷歌改变他们的衡量标准，专注于移动优先，这迫使许多开发人员改变他们制作网站的方式。同样的，感觉无障碍目前也在经历这种变化。为了减少压力，第一步是理解度量标准，以及如何达到它。有几个地方可以这样做。最受欢迎的工具之一是谷歌的 Lighthouse，它易于使用，许多开发人员已经用它来测试他们的速度。以下是你如何使用 Lighthouse(你需要安装 Chrome 的开发版本):
1)打开 Chrome dev
2)转到你的网站
3)打开开发工具(与检查页面相同)
4)导航到审计
5)点击审计
6)完成
这个工具非常有用，有几个原因:它帮助你了解谷歌认为什么对帮助你的排名是重要的，它使用起来非常直观，它是免费的，它还可以帮助你找到创建你的网站的道路你也可以使用许多付费服务。
好吧，太棒了，你已经知道我们的可访问性得分是多少了。如果分数不是很大你会怎么做？首先，您可以查看一些资源，并找出可以采取哪些措施来修复它。你可以去 w3c 的网站寻找很多有用的工具，或者去 a11y 的网站寻求帮助。我个人最喜欢的，但可能是最难完成的是实际的用户测试。如果你选择的任何验证工具表明你的网站不能被只使用键盘的人访问，你认识这样的人吗？如果你不这样做，也不是世界末日，因为许多其他开发者也遇到了同样的问题。Chrome 有很多插件可以让你看到你的网站对残疾人来说是什么样子。例如，它将向您展示您的网站对色盲人士来说是什么样的。为了避免这篇文章过于沉重，firefox 还发布了一个可访问性检查器，这是另一个有用的工具(另外你还可以免费进行一些跨浏览器测试)。为了结束这篇文章，我想快速浏览一些在你的网站上实现起来并不复杂的技巧。让你的文字有高对比度。有很多工具可以检查这一点，让你的文本清晰易读是一个很好的设计，对于手机用户来说也更容易。你的文字也应该易于理解。这并不意味着降低你的文本，而是要清晰简洁。这也将有助于你的搜索引擎优化，因为大多数蜘蛛不够“聪明”,不能在高层次上阅读。另一个有助于 SEO 的技巧是给所有有意义的图片添加 alt 标签。这样做也能让你的网站对屏幕阅读器用户更友好。最后，回到指标上来，你的速度指标会影响你的可访问性。例如，如果某人只有一台旧设备，而你的网站又大又慢，他们根本无法访问。
我希望这给了你一些工具和技巧来实际实现可访问性，而不只是想想而已(比如最新的 js 框架)。