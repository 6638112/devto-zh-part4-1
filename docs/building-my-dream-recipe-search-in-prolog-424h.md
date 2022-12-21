# 在 Prolog 中构建我的梦想食谱搜索

> 原文：<https://dev.to/valeriecodes/building-my-dream-recipe-search-in-prolog-424h>

我在 [Recurse 中心](https://www.recurse.com/)的 12 周疗程已经过半。在这里，我一直试图扩展我的编程视野，超越我的 Rails web 开发，面向对象为中心的世界。这包括探索[自然语言处理](https://dev.to/valeriecodes/exploring-natural-language-processing-with-alice-in-wonderland-ldc)，硬件黑客，离线优先应用，以及愚蠢的纯 CSS 艺术字，等等。

我和这里的其他几个人一起在 7 周内完成了《7 种语言》这本书，本周我们遇到了《T2》Prolog 编程语言。

Prolog 不同于我以前遇到过的任何语言。它是一种声明性的语言，而不是过程性的语言，所以你不用编写如何完成某件事情的步骤，而是给它事实和规则，然后它可以根据这些事实和规则执行查询。在 Dev 和 T2 上有很好的序言教程[，我在这里不打算写了。](https://dev.to/matchilling/introduction-to-logic-programming-with-prolog-cdh)

大概是这样的:

```
parent(fantine, cosette).

child(X, Y):-
  parent(Y, X) 
```

上面写着“芳汀是珂赛特的父母。”并且如果 Y 是 X 的父，则确定 X 是 Y 的子。然后我们可以运行以下查询:

```
?- parent(fantine, cosette).
true
?- child(cosette, fantine).
true
?- child(cosette, Who).
Who = fantine 
```

在最后一个例子中，我们实质上是在问“珂赛特是谁的孩子？”Prolog 向变量`Who`提供一个可能的值作为解决方法。

如果您想在浏览器中更多地使用 Prolog，您可以在此页面中使用[。](https://swish.swi-prolog.org/)

这本书探讨了如何用这种语言来协调海豚训练员的时间表和编写数独解算程序，但我已经太专注于我的白鲸了🐋(双关语):举办一场完美的晚宴。

所以我想，“如果我能以事实的形式向 Prolog 提供我最喜欢的食谱，然后根据我拥有的时间量或我在食品室中拥有的物品进行查询，会怎么样？”

我开始研究蓝莓松饼的配方。

```
recipe(muffin).

contains(blueberries, muffin).
contains(milk, muffin).
contains(butter, muffin).
contains(eggs, muffin).
contains(salt, muffin).
contains(sugar, muffin).
contains(flour, muffin).
contains('baking powder', muffin).

diet(vegetarian, muffin).
diet(nut-free, muffin).

minutes_to_prepare(40, muffin).

meal(breakfast, muffin).
meal(snack, muffin).
meal(dessert, muffin). 
```

我对另外几个食谱也这样做了，很快我就能够构建类似于
的查询

```
?- diet(vegan, First), meal(appetizer, First), 
meal(dinner, Second), contains_ingredients(Second, [basil, zucchini]), 
meal(dessert, Third). 
```

翻译成简单的英语:素食开胃菜，含有罗勒和西葫芦的晚餐，以及甜点。

然后，Prolog 给出了一个菜单建议:

```
First = gazpacho,
Second = 'summer pasta',
Third = muffin 
```

如果有多个满足约束的菜单，您可以再次运行它来查看其他选项。

当然，这离一个特别友好的用户界面还有很长的路要走，但让我想到了所有可以实现的可能性，来制作我梦想中的食谱搜索工具。[这里有一个要点](https://gist.github.com/valeriecodes/7802d297f639d087fe7e624a31951ac8)和这里使用的代码。🥣🍝🍰