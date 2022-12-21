# 编程和开发的规则和提示

> 原文：<https://dev.to/pcmichaels/rules-and-tips-for-programming-and-development-2o23>

当我在大学学习 Pascal 的时候，我写了一个“编程的 10 条戒律”作为给自己开的一个玩笑。它从来没有像互联网那样传播得那么远。这是 Borland 的涡轮帕斯卡的日子；最新的技术是室内厕所，钱可以买到的最贵的调制解调器是 14.4kbps！

我想我应该为现代起草一个类似的想法。希望有人会觉得这很有趣。请随意添加您自己的。

1.永远不要使用 *goto* 语句([，即使 Asp。Net 核心代码千疮百孔](https://github.com/aspnet/AspNetCore/blob/b23ea5b6683b08e8d168ccf49e0fc8515077ee2e/src/Mvc/Mvc.Core/src/Infrastructure/ControllerActionInvoker.cs)。

2.成为代码审查/拉取请求的一部分意味着您的代码可以工作——即使作者或审查者都没有真正看过代码。这就是公关的魔力。

3.下面的咒语意味着代码将在未来的某一天神奇地出现:

```
 // ToDo: [anything can go here - even if it makes no sense!] 
```

4.如果有人问你你的代码是如何工作的，而你不知道如何工作，不要担心:只需使用 Ctrl-Tab 键切换代码窗格，并使用像“推”、“吸”、“喷”这样的词；比如:“这个段从某个地方吸取变量，推到另一个地方，在那里喷出来。”

5.尽可能多地提到“设计模式”这个术语(即使你不知道它的意思)，只要有可能，说出敏捷宣言上的名字。你提到他们时会得到额外的加分，就好像你认识他们一样:“鲍勃叔叔对这件事的看法是……”或者“福勒说你应该……”

6.自信就是一切。即使你已经为一个问题纠结了好几天，每当你被问及还有多长时间，你必须给出并回答几个小时。此外，永远不要承认在任何事情上花了超过两个小时。试试这张方便的图表:

> “快完成了”:“我已经花了一个星期，我不知道为什么它不工作。”

> “今天早上我会把它做完的”:“还有一周的工作要做。”

> “我会说这是几个小时的工作”:“要求是如此模糊，可能是 20 分钟到 5 年的任何地方。”

> “不到半小时”:“我昨天做了这个，所以我今天会提前半小时完成。”

7.不要让你的简历过时。如果你觉得*正在做*正在做的事情，你应该尽快联系你的直线经理，建议用最新的 Javascript 框架重写。您可以尝试以下方法:

> "我们需要用 bananagrape.js**替换这个传统的*角度系统."
> 
> * Legacy 可用于描述任何在超过 5 分钟前*启动*的代码。
> 
> **如果 bananagrape.js 是真实存在的，那么我希望对我的想法进行某种形式的补偿！

8.只有 35 岁以上的开发人员使用 Visual Studio。其他人都使用定制黑暗主题的 VS 代码。

9.永远不要对单元测试进行代码审查:单元测试已经被自动编写的事实本身就说明它是正确的，不管代码是多么的模糊和混乱。

10.没有必要真的去阅读[敏捷宣言](https://agilemanifesto.org/)。即使你练习‘敏捷’。最好要求被派去参加为期一周的培训课程；毕竟，你不能在简历上写“阅读敏捷宣言——50 个单词”，但是“认证 Scrum Master”看起来很棒。