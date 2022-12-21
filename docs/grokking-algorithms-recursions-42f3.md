# 搜索算法-递归

> 原文：<https://dev.to/jasterix/grokking-algorithms-recursions-42f3>

成为一名 JavaScript 忍者的一部分是在某种程度上精通处理算法，或者我称之为“一口大小的诡计”。

作为一个相对的初学者，我已经遇到了看似相同的 10 个问题，只是形状、颜色和大小不同，也就是难度不同。

花了 4 个小时努力解决这个问题让我意识到，当谈到算法时，我不知道从哪里开始。虽然 Flatiron 给了我一套很棒的基本工具，但这些工具，或者更确切地说，我习惯如何应用它们，并不总是最适合解决 [LeetCode 问题](https://leetcode.com/jasterix/)。

所以我决定学习 Aditya Bhargava 的算法。这本书已经向我推荐过几次，但我最初选择了边做边学，不太成功。

尽管如此，我还是决定从第 3 章开始:递归。

#### 这里是我关于递归的三点心得

1.  递归是指函数调用自己
2.  每个递归函数有两种情况:
    1.  基本情况–函数完成执行和
    2.  递归情况——函数调用自己
3.  这意味着当每个函数调用进入调用堆栈时，这些函数调用直到满足基本情况才完成

在你当地的图书馆或亚马逊上查看搜索算法