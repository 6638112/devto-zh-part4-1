# 在发布新功能之前

> 原文：<https://dev.to/vinistock/before-shipping-a-new-feature-p28>

# 简介

发布新功能令人兴奋，作为软件开发人员，我们希望看到我们的代码在生产中运行。但是，在交付任务之前，可以采取一些行动、问题和步骤，这将有助于提高新功能的质量。

行为，比如为正常的失败构建代码，利用重构的机会，理解被交付的特性的影响，监控和手动测试变更，仅仅是发布前活动的几个例子。

# 交付功能前要问的问题

务必时刻牢记新变化可能给最终客户带来的影响。思考如果出错，不管合并的提交有多简单，用户会有什么后果。

此外，根据最终用户的观点，思考交付给他们的功能有多重要。怎样才能做的更好？

在发布我们心爱的代码之前，可以问几个问题:

> 如果这个页面/服务中断，用户会有什么体验？
> 
> 恢复这些变化有多困难？
> 
> 像这样的中断会对我们的品牌形象产生多大的影响？
> 
> 还有哪些功能可以利用这一点，为我们的用户提供更多价值？
> 
> 此功能中可能缺少什么功能？

对这些问题的回答将概括出可以用来提高已发布特性质量的步骤。

# 发货前清单

下面是在单击部署按钮之前可以完成的操作的清单。

## 为有影响的边角案例创建测试

当然没有必要测试每一个边缘案例。您很可能不会覆盖所有的内容，这会让您的测试套件变得臃肿。

但是，导致严重故障的极限情况必须经过测试，并包含回退功能。例如，如果特定页面依赖于从外部 API 获取数据。如果 API 关闭会发生什么？这一页会断吗？它是部分填充的吗？它会重定向到不同的页面吗？

探索这些最具影响力的边缘场景通常可以防止未来的生产难题。如果有一个人疏忽了，在测试中重现错误，修正不希望的行为，然后把它推到堆栈上。

## 手动测试修改

不幸的是，自动化测试并不总是能捕捉到一切。花时间探索产品和交付的新特性。像客户一样体验，问问自己是否对解决方案满意。

如果确定了与该特性相关的改进，确保用用户故事来跟踪它们。它们可能不需要立即实现，但是如果它们在 backlog 中是可访问的，最终它们会被处理。

## 得到顾客的反馈

对于我们开发的产品应该如何使用，我们经常有想法和意见。然而，真正重要的是我们的客户如何使用和感知我们提供的功能。

从最终用户那里得到反馈是一种苦乐参半的感觉。它可以同时具有挑战性和洞察力。他们可能会批评你努力打造的产品，同时也让你知道他们需要什么或对它有什么期望。思想开放，必要时准备转移注意力。

## 设置充足的监控

在软件领域，很多事情都发生在幕后。仅仅通过摆弄用户界面来判断是否一切正常远非易事。日志记录是用来窥视生产中运行的系统并了解事情是否真的正常的方法之一。

但是你会记录什么呢？这不是一个无关紧要的问题。这取决于系统、产品和开发团队。过多的日志记录可能会导致不必要的开销，而过少的日志记录将会使您对应用程序中发生的事情一无所知。

要记录的内容示例如下:

*   当预期错误发生时(例如:内部营救/捕捉块)
*   当一个不希望但必要的行为发生时(例如:用户被重定向到 404 页面)
*   关键指标(例如:后台处理的项目数量)
*   业务指标(例如:使用谷歌注册的用户数量)

## 重构代码

偶然发现可以重构的代码片段(出于质量或可重用性的目的)经常发生。改进代码或使其可被其他开发人员重用现在可能会花费一点时间，但从长远来看是值得的。

如果没有开发人员愿意为重构代码付出代价，技术债务就会越积越多，直到代码库减缓新功能的开发。在这一点上，你正在为所有没有完成的重构付出代价。

如果一段代码可以通过一些额外的工作来改进，那就去做。让下一个接触这部分代码的开发人员更开心。

# 结论

这是我对功能发布清单的看法。你会在清单上添加什么？你的团队有哪些实践？我很想听听！