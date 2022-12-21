# 在 JavaScript 中反转字符串

> 原文：<https://dev.to/benhaugen/reversing-a-string-in-javascript-27oe>

我打算每周写一篇博客，讨论编码面试中的一些常见问题。他们将从非常基础的开始，并从那里进步。在求职过程中继续练习求解算法很重要，否则你自学或在训练营学到的知识会比你想象的消退得更快。

在面试初级网站开发职位时，最常被问到的问题之一是如何反转字符串。事实上，在 JavaScript 中有很多反转字符串的方法，有些方法肯定比其他方法好，但是今天我们只学习两种最简单的方法。

# 快捷方便

反转字符串最简单的方法是使用内置的 JavaScript 函数。如果你在面试中用这种方法解决了这个问题，一定要让面试官看到，没有这些内置功能你也能解决这个问题。这样展示你知道怎么解也无妨，因为这证明你知道一些基本的函数。现在让我们开始吧。

我们将要使用的三个 JS 方法是。split()，。反转()和。加入()。这些方法定义直接来自 MDN Web 文档，这是所有 JS 方法的一个很好的来源。

*   split()方法通过将字符串分割成子字符串来将字符串对象分割成字符串数组，并使用指定的分隔符字符串来确定每次分割的位置。

*   reverse()方法原地反转数组。第一个数组元素成为最后一个，最后一个数组元素成为第一个。

*   join()方法通过连接数组(或类似数组的对象)中的所有元素，用逗号或指定的分隔符字符串分隔，创建并返回一个新字符串。如果数组只有一项，则该项将在不使用分隔符的情况下返回。

如果我们想要反转字符串“恐龙”，我们实际上可以将下面的三个方法链接在一起，就像这样:

[https://repl.it/@ben1232jazz/Short-Reverse-String?lite=true](https://repl.it/@ben1232jazz/Short-Reverse-String?lite=true)

# 使用 for 循环

面试官想要看到你知道如何写一个简单的 for 循环，所以告诉他们你知道如何写。首先，你需要设置一个等于空字符串的变量，这样你就可以在 for 循环之后添加它。在编写 for 循环时，记住要从字符串的末尾开始。因此，不是典型的 i = 0，而是希望从最后一个索引开始，这可以通过 i = str.length - 1 来实现。记住，我们想在这里减少 I，因为我们想从结束到开始。

在 for 循环中，我们希望添加开始时创建空变量。添加到我们的空变量的快捷方式如下所示:reversed += str[i]。

不要忘记在 for 循环完成后，在我们的函数中返回变量。它应该是这样的:

[https://repl.it/@ben1232jazz/Longer-Reverse-String?lite=true](https://repl.it/@ben1232jazz/Longer-Reverse-String?lite=true)

这是非常基本的东西，但是要确保你记住它，并且每天练习你的算法。有时候，我们为了获得面试机会付出了太多的努力，以至于当我们最终获得面试机会时，我们已经忘记了一些基本的东西。不要让那发生在你身上！