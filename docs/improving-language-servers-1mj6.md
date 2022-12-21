# 改进语言服务器

> 原文：<https://dev.to/jwoudenberg/improving-language-servers-1mj6>

语言服务器很棒，但我们可以做得更好。语言服务器是一个程序，它知道许多使用编程语言的技巧。假设您想要重命名项目中的一个变量。你点击一个菜单或者按一个热键来发送指令给你的编辑，然后你的编辑可以把工作委托给一个语言服务器。

语言服务器的伟大之处在于，它们提供了为 Atom、VSCode、Sublime、Vim、Emacs 和其他编辑器编写独立语言插件的替代方案。相反，我们可以为一种编程语言建立一个单一的语言服务器，让它变得更好，并且在所有的编辑器中都支持这种语言！

要为编程语言创建语言服务器，您需要实现“语言服务器协议”的一部分。该协议定义了程序员可能执行的不同技巧，如重命名变量。语言服务器不需要实现整个协议，因为不是所有的技巧在所有的语言中都有意义。

## 缺点

尽管语言服务器很棒，但我不太喜欢它们的某些方面。一个是向程序员展示所有的语言服务器功能需要大量的菜单空间或热键。无论哪种方式，程序员都需要一个好的记忆来记住如何触发每一个可用的技巧，而我的记忆力不是很好。

令我更失望的是，语言服务器协议在支持常见编程语言技巧方面大放异彩。重命名变量就是这种常见技巧的一个例子，因为我们几乎在任何编程语言中都要用到它。一种语言独有的特性不太可能有语言服务器协议支持，我认为这是一种耻辱。我希望我的语言工具在语言本身闪耀的地方闪耀！

## 一种面向错误方向的抽象

语言服务协议是一种抽象。抽象就像小巷里试图向你推销东西的可疑人物。这个人说:“嘘，你知道所有的编程语言都是一样的吗？他们支持同样的一些把戏。”我们知道这种说法是不正确的，编程语言有很大的不同！语言服务器是一个很好的例子，说明抽象尽管是一个谎言，但仍然是有用的。

这是另一个抽象:“嘿，你，听着，所有的编辑都是一样的！您可以在其中打开文件，然后更改这些文件的内容。就是这样！”。另一个错误的说法是有时关于哪个编辑是最好的激烈争论。不过，我认为编辑器之间的差异比编程语言之间的差异要小。让我们把这个想法付诸实践。

回想一下，语言服务器就是能够为一种语言编写一次工具，然后能够在所有编辑器中使用这种工具。它通过抽象编程语言来做到这一点。如果我们将编辑器抽象化会怎么样？

## 编辑驱动程序

为了创建一个抽象编辑器而不是编程语言的协议，编辑器和语言服务器需要使用不同的语言，一种不使用编程语言术语的语言。首先，当用户做一些有趣的事情时，比如保存文件或悬停在特定的行和列上，编辑器应该向语言服务器发送通知。然后，语言服务器可以选择通过向编辑器发送指令来做出响应，比如更改文件或移动光标。

我们称通知和请求编辑器支持“编辑器驱动协议”，因为它们支持外部程序驱动编辑器。外部程序不需要知道它正在驱动哪个编辑器，这是我们的编辑器抽象在起作用。这个“编辑器驱动协议”可以取代我们今天使用的“语言服务器协议”。

让我们看看在这个系统中变量重命名可能是什么样子。为了开始重命名，程序员改变程序中变量的任何使用并保存。语言服务器收到程序员所做更改的通知。它看到程序员在一个地方重命名了一个变量，并对该变量的所有其他使用执行相同的重命名。

## 改善与否？

让我们考虑一下这种语言服务器的替代方案与原来的相比如何。第一个问题是，我们是否仍然可以编写一次语言服务器，并在编辑器之间重用它。答案是肯定的:我们的语言服务器将使用标准化协议与任何编辑器通信，就像现在一样。

我指出的第一个语言服务器协议的缺点是，它要求程序员熟悉一堆菜单或热键。编辑器驱动协议解决了这个问题，并允许我们建立更好的交互。在这个例子中，我们看到用户可以在不点击任何菜单中的“重命名”或者不需要使用热键的情况下执行重命名。他们只是开始做一些改变，然后语言服务器就完成了。程序员可以发现重命名功能是他们工作的一个自然部分。

我提出的第二个语言服务器协议缺点是，语言服务器协议不支持与使编程语言独一无二的属性相关的技巧。编辑器驱动方法没有这种限制。它可以回答特定于语言的查询，并执行特定于语言的重构。关于特定于语言的工具功能的一些例子，请查看关于 [elm-pair](https://elm-pair.jasperwoudenberg.com/) 的提议，这是一个基于编辑器驱动方法的 elm 语言服务器。

这也有不好的一面。在变量重命名的例子中，有一个自然的钩子触发了语言服务器:程序员在一个地方改变了变量的名称。对于语言服务器可能想要支持的每一个技巧，可能都没有一个好的挂钩。一个曲解程序员意图的语言服务器将是令人讨厌的，而不是有益的。当使用编辑器驱动程序方法时，好的语言服务器设计的标准更高。

另一个缺点是我们现在抽象了编辑。在旧的方法中，我们很难支持特定于语言的特性，而现在我们很难支持特定于编辑器的特性。例如，编辑器 VIM 支持不同的模式。VIM 的语言服务器协议实现可能会在某些情况下改变编辑器所处的模式，但是编辑器驱动程序协议实现不会支持特定于一个编辑器的功能。

## 结论

语言服务器使我们能够为所有编辑器编写一次编程工具。我们可以通过抽象编辑器而不是编程语言来改进这个概念。这导致了新的设计挑战，但是当克服这些挑战时，可以创建令人愉快的工具，这些工具可以被发现并发挥每种语言的优势。