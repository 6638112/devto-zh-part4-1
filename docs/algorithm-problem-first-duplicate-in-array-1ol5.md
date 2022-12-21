# 算法问题:数组中的第一个重复项

> 原文：<https://dev.to/kalkwst/algorithm-problem-first-duplicate-in-array-1ol5>

我们得到了下面的问题陈述。

> 给定一个数组`a`，它只包含从`1`到`a.length`的
> 范围内的数字，为第二次出现的索引最小的
> 找到第一个重复的**数字**。换句话说，如果
> 有 1 个以上的重复数字，则返回第二次出现的
> 的**数字**，该数字的索引小于另一个数字的第二次出现的
> 的索引。如果没有这些元素，
> 返回`-1`。

所以本质上，我们需要搜索数组并找到第一对重复的元素。有几种方法可以解决这个问题，让我们来看看其中的一些。

## 方法 1:简单循环方法

第一种也是最直观的方法是选择一个元素，一直迭代到数组的末尾，检查该元素是否有重复。

这样的算法是如何工作的？首先，我们选择第一个元素
的**,并一直查看列表的末尾。如果我们发现一个元素
是重复的，我们就返回这个元素并在这里停止。如果我们不
，我们做同样的步骤，但是从
列表的第二个**元素**开始。我们继续这样做，直到到达数组的倒数第二个**元素
。如果到目前为止我们没有发现任何重复的元素，
那么就没有重复的元素，我们应该返回 *-1* 。我们在这个元素处停止
,因为这是我们找到副本的最后机会。如果
最后一个元素有副本，我们应该已经找到了。****