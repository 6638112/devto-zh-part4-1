# 调试的 10 个技巧

> 原文：<https://dev.to/fishj123/10-tips-for-debugging-3pci>

我花了大量时间调试我的应用程序。因此，我决定列出我解决错误的常用方法，现在我用它作为调试时的参考/提醒。我将分享我在这篇文章中的 10 个步骤，以及每个步骤的一些解释。本文的目标读者是初学者或处于开发生涯早期的人。

将问题分解成可管理的小块
这是调试/解决问题时最重要的建议。我相信你已经听过无数次了，但提醒一下这其中的价值也无妨。如果你试图解决一个 bug，那么你必须有条不紊，一步一步来。例如，如果您试图调试应用程序中的 click 事件，那么首先要将 console . log(“clicked”)添加到 click 事件应该调用的函数中，以确保它被调用。

**Console.log()**
这引出了我的第二个技巧，利用 Console.log()。一些开发人员喜欢嘲笑那些过度依赖 console.log()进行调试的人，但是我认为这是快速了解应用程序实际在做什么的最有效的方法之一。如果你从一个 API 中获取一些数据，并在你的应用中操作它，在那里放一个 console.log(data ),以确保你所获取的绝对是你所想的。

**阅读错误信息**
这是一个初学者有时会纠结的问题。有时，问题的答案就在你面前，在错误消息中。您的错误消息将告诉您导致错误的代码行，以及出错原因的简短描述。有时消息有点晦涩，需要一些经验来理解它的真正含义，但是你越注意错误消息的内容，你就能越快地学会解密它。

注释掉代码
这是我最喜欢的调试应用程序的方法之一，原则是通过注释掉你怀疑可能涉及的代码块来排除不是导致错误的原因。如果您注释掉了一些代码，错误仍然出现(并且没有改变),那么问题很可能不是由代码块引起的。这个排除过程可以帮助你很快找到问题的根源。

再次检查你正在做的事情
这是一个在调试过程开始前做的好事情。我的意思是，确保你正在处理的代码是你认为的那样。例如，有时您可能试图修复开发环境中的一个错误，同时疯狂地刷新活动环境中的页面，并想知道为什么您的更改都不起作用。

忘记你的假设
如果你发现自己说“这部分代码不会是我的错误的原因”，而没有实际检查它，那么你正在为自己设置一个痛苦的世界。我的建议是，当你坐下来调试应用程序时，永远不要想当然。我的大多数错误来自于我对我指示应用程序去做的事情与我实际上指示它去做的事情不一致的理解。

学会使用调试器
如果你花时间去了解如何使用调试器，那么你一定会看到它的好处。调试器就像类固醇上的 console.log()，你可以在整个代码中放置断点，以查看运行时到底发生了什么。用它来查看变量的值，函数被调用的顺序等等。绝对值得投入时间去学习它。

谷歌 it
人们可能已经说过一千遍了，要成为一名优秀的程序员，你只需要擅长谷歌搜索。我发现谷歌对语法错误等小错误很有用。但是随着你的 bug 变得越来越复杂，它就失去了价值。这仍然是值得做的，因为毫无疑问，有人会有同样的问题，你在过去有。

这是我得到的最好的调试建议。我不知道有多少次，我在一个错误上花了几个小时，当我停止调试它时，才意识到解决方案是什么。休息 15 分钟去散步对你的大脑有奇效。让你的思想漫游可以加速找到解决方案的过程。我现在试着把自己的调试时间限制在一个小时以内——如果一个小时后我还找不到答案，那么我会休息一会儿，清醒一下头脑，然后再回到电脑前。

**寻求帮助**
我调试过程的最后一步是寻求帮助。寻求帮助绝对没有什么丢人的。如果你打算把整个职业生涯都花在编程上，从其他程序员那里获得帮助是必不可少的。如果有任何人从来没有因为一个 bug 而向别人寻求帮助，我会感到很惊讶！你越早克服对接触他人或看起来愚蠢的恐惧，你就越早成为一名程序员。另一方面，我鼓励你帮助别人解决他们的问题，帮助别人感觉很好，你也可能从中受益。毕竟，巩固你的知识的最好方法是教别人。

我的调试列表就这样了。希望你们中的一些人会觉得它有用，如果你有任何你自己的建议，你认为我应该利用，那么我很乐意听听！