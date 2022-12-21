# TPP 主题 8:优秀设计的本质

> 原文：<https://dev.to/steadbytes/tpp-topic-8-the-essence-of-good-design-2iok>

> 这篇文章最初出现在[steadbytes.com](https://steadbytes.com/blog/the-pragmatic-programmer-20th/topic-8-challenges/)
> 
> 见实用程序员 20 周年纪念版系列[第一帖](https://dev.to/steadbytes/the-pragmatic-programmer-20th-anniversary-edition-series-1e2l)介绍。

## 挑战 1

> 想一个你经常使用的设计原则。是为了让事情变得容易改变吗？

纯函数！在[功能编程](https://en.wikipedia.org/wiki/Functional_programming)之外，这可能是一个较少使用/考虑的设计原则——经常被诸如[固体](https://en.wikipedia.org/wiki/SOLID)和[干燥](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)之类的原则所取代。然而，我发现不管使用什么样的编程模式，这都是一个非常有效的原则。

> 在计算机编程中，纯函数是指具有以下性质的函数:
> 
> 1.  对于相同的参数，它的返回值是相同的(本地静态变量、非本地变量、可变引用参数或来自 I/O 设备的输入流没有变化)。
> 2.  它的求值没有副作用(没有局部静态变量、非局部变量、可变引用参数或 I/O 流的突变)。
> 
> ——纯函数，[维基百科](https://en.wikipedia.org/wiki/Pure_function)

这无疑使代码更容易更改。由于一个功能只依赖于它的输入，它可以独立于周围系统的而被理解*。这意味着，例如，函数可以在知道它不会通过共享的、可变的状态破坏其他东西的情况下被改变。*

## 挑战 2

> 还要考虑语言和编程范式(OO、FP、Reactive 等等)。当涉及到帮助你编写 ETC 代码时，有没有什么好处或坏处？有人两者都有吗？
> 
> 编码时，你能做些什么来消除消极因素，突出积极因素？

我将只讨论几个范例的几个要点——这本身可能是一整本书！请注意强调诸如“它能”和“理论上”这样的短语。这些都不是绝对的真理，我不相信任何编程范式是完全不正确或糟糕的。这些是根据我的经验对每一个问题的正面和负面的务实评估。

### 面向对象

#### 正

类*可以*将软件分割成小块的功能/行为。每一个都提供了一个接口，其他类可以使用这个接口来实现那个类的*行为*，而不需要理解用来实现它的算法。这在*理论*中，通过隐藏*抽象*背后的细节，允许这些类的内部发生变化，而不需要改变系统的其余部分，从而使软件更容易理解。

#### 负

实际上，对于任何重要的场景来说，将软件的行为分割成离散的类都变得很困难。这经常会导致[泄漏的抽象](https://www.joelonsoftware.com/2002/11/11/the-law-of-leaky-abstractions/)和复杂的[继承层次](https://en.wikipedia.org/wiki/Inheritance_(object-oriented_programming))——这两者都使得代码**随着时间的推移更难更改**和管理。

### 功能性

#### 正

一个程序被模拟成许多小功能的组合。这些函数中的每一个都对一些数据执行一个小的操作(通常是纯操作)。因此，程序是一组数据的*转换*，每个转换都可以很容易地推理出来。这种组合设计可以使改变程序变得简单——用另一个函数组合一些函数来产生不同的输出。

#### 负

由于大量的小函数，很难找到在哪里改变代码来影响预期的行为改变。此外，*可能*很难改变程序中的底层数据。由于功能程序是对一些简单数据结构的一系列转换，向这些*添加新的键和/或值会*导致整个程序的级联变化。当然，有很多方法可以设计出一个不属于这种情况的程序，但是这需要很多技巧和经验来有效地完成。

### 程序化

#### 正

一个程序从上到下阅读，理论上可以理解程序执行的过程/步骤。这可以使改变变得容易，因为程序中的每个步骤发生在哪里以及如何工作都很清楚。

#### 负

对于任何重要的场景，过程化程序很容易陷入[意大利面条代码](https://en.wikipedia.org/wiki/Spaghetti_code)的陷阱。此外，由于算法和每个步骤的内部工作细节是存在的，所以很难从低级细节(“如何”)中解析出高级步骤(“什么”)。

## 挑战 3

> 许多编辑器都支持(内置或通过扩展)在保存文件时运行命令。让你的编辑器弹出一个 ETC？消息，并以此为线索来思考刚刚编写的代码。容易改变吗？

在 Ubuntu(和大多数 Linux 发行版)上使用 [Vim](https://www.vim.org/) ，这可以通过使用[自动命令](http://vimdoc.sourceforge.net/htmldoc/autocmd.html)和[通知-发送](http://manpages.ubuntu.com/manpages/xenial/man1/notify-send.1.html)来实现:

```
:autocmd BufWritePost * !notify-send "ETC?" 
```