# 你可以写工作代码。接下来是什么？

> 原文：<https://dev.to/peteratticusberg/you-can-write-working-code-what-comes-next-21j1>

设计决策。或者至少，它们是接下来的事情之一。

代码要么有效，要么无效。在设计决策中，事情并不是非黑即白的。Alice 决定使用 redux 来存储 react 应用程序中的所有状态。John 决定使用 ECC 而不是 RSA 进行加密。Sarah 创建了一个用户表来存储 3 种不同类型的用户。

这些是好的决定吗？

我们无法知道。

代码永远是达到目的的手段。它本身从来都不是目的。当我们决定如何构建它时，需要根据代码的目的对它们进行评估。我们不知道爱丽丝、约翰和莎拉是否做出了正确的选择，因为我们不知道他们在建造什么以及为什么建造。

* * *

例如，假设 Alice 第一次使用 redux 进行一个辅助项目。这增加了她的应用程序的复杂性，比她没有使用 redux 时更难理解和使用。

使用 redux 是一个好的选择吗？我们可以说(在这种情况下),使用 redux 增加了项目的完成时间和维护成本。我们也可以说它帮助了爱丽丝学习 redux。

假设 Alice 的目标是学习 redux。维护不是问题，因为她不打算维护这个项目，完成时间也不是问题，因为她有很多无组织的空闲时间。在这种情况下，公平地说，考虑到这个目标，使用 redux 是一个很好的选择，负面影响最小。

在另一个场景中，假设 Alice 的目标是尽可能快地向客户交付一个易于维护的工作应用程序。在这里，可以说，考虑到这个目标，使用 redux 是一个糟糕的选择，因为它增加了完成时间和维护成本。

在公司，事情变得更加复杂。有多个相互竞争的目标。首席执行官希望尽快启动。首席技术官想要可维护的代码和最小的技术债务。产品团队想要一个大的特性集。设计想要像素完美，跨浏览器兼容。

时间和资源都是有限的，因此业务部门必须确定优先级。然后，这些优先级成为在代码中做出设计决策的基础。(注意:在理想情况下，这些决策在工作分配给工程师时就已经确定了，但实际上通常不是这样)

* * *

要成为一名高效的软件开发人员，您需要确保您所做的设计决策符合代码上下文之外的优先级。

如果你是开发新手，这看起来令人生畏，不要担心——这是所有开发人员一直在磨练的技能。简单地意识到这是一个成长的领域，随着你作为开发人员获得越来越多的经验，你将能够培养这种技能。