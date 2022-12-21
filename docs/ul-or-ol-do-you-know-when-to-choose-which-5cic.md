> 原文：<https://dev.to/rikschennink/ul-or-ol-do-you-know-when-to-choose-which-5cic>

何时将信息标记为列表？这似乎是一个简单的任务。但是如果你已经做了一段时间，你的大脑会开始到处看到列表。接下来的几个技巧可以帮助您决定信息是否应该被标记为列表，如果是，那么这个列表是无序的还是有序的。

## 你在看单子吗？

如果信息由一组相似的条目组成，那么它应该被标记为一个列表。例如，搜索结果或导航项目。有时候，当把一个视觉设计转换成 HTML 时，你可能会注意到每个元素集合开始感觉像一个列表。当你感觉自己处于那种情况时，问问自己:

“屏幕阅读器软件应该宣布项目的数量吗？”

如果是的话，你看到的信息肯定是一个列表。

另一种方法是问自己，如果列表中的项目用项目符号或数字标记会不会很奇怪(trick by [@stommepoes](https://twitter.com/stommepoes/status/773123776120811521) )。如果不奇怪的话，我们手上有一份名单。

## 列表应该排序吗？

现在我们已经找到了一个列表，我们需要决定它是有序的`<ol>`还是无序的`<ul>`列表。

[w3 规范陈述了以下关于有序列表的内容](https://www.w3.org/TR/html52/grouping-content.html#elementdef-ol):

> 一种列表，其中的项目是有目的地排序的，因此改变顺序会改变列表的含义。

如果改变列表的顺序导致列表丢失任何有意义的数据，那么它应该被标记为有序列表。

例如，以下列表应格式化为`<ol>`

*   搜索结果(假设它们由相关性返回)。打乱列表中的项目，你会突然无法确定每个项目的相关性。
*   文章评论。打乱注释会导致引用早期注释的注释失去意义。
*   宜家家具说明。

如果列表在移动项目时没有丢失信息，那么使用`<ul>`而不是`<ol>`元素是安全的。

就这样，你现在拥有了超能力来决定是否应该将一些信息标记为列表。如果你有任何问题，请告诉我，乐意在下面回答。