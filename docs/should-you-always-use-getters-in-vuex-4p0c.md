# 在 Vuex 中应该总是使用 getters 吗？

> 原文：<https://dev.to/firstclown/should-you-always-use-getters-in-vuex-4p0c>

关于 Vuex 一次又一次出现的一个问题是“我在访问数据时总是使用 getter 吗？或者我可以直接访问原始状态吗？”这是你听说的你应该做的事情之一，但似乎没有人真正解释为什么。您真的需要为存储的每一条数据创建一个 getter 吗？那不就是一堆不需要的样板和重复吗？

## 可以从一个组件直接访问 Vuex 状态吗？

所以，首先从技术上回答:没有什么能阻止你直接在组件中访问状态。事实上，如果您愿意，可以直接在组件的 UI 中完成。

```
<template>
    <p>
    {{ $store.state.clickCount }} clicks!
  </p>
</template> 
```

Enter fullscreen mode Exit fullscreen mode

或者在任何 Vue 方法或计算属性中。直接状态读数 100%可用。

## *是否应该*从一个组件直接访问 Vuex 状态？

这是一个有点不同的讨论。仅仅因为你*能*做某事并不意味着你*应该*做某事。至少，我妈妈总是这么告诉我。当我意识到我可以用吸管喝激浪时，我才艰难地发现了这一点。我连续这样做了几天，很快意识到有些事情就是不该做。

直接访问 Vuex 状态是其中之一吗？应该直接访问状态吗？

### 不，不应该

这就是我认为的 Java 方法。在 Java 中，对对象变量的所有数据访问都是通过所谓的 Getters 来完成的。(听着耳熟？)的想法是，允许直接访问实例变量是一个坏主意。如果您想在将来的某个时候改变实例变量的表示方式，该怎么办呢？如果你想锁定谁可以设置它呢？如果您想在可以设置的值周围添加验证，该怎么办呢？

以上所有这些都会破坏[封装](https://en.wikipedia.org/wiki/Encapsulation_(computer_programming))，这是一件非常糟糕的事情。许多程序员被这种想法所吸引:你必须让数据访问通过一个函数，这样程序员就可以一直控制数据的访问方式。您可能有一个只返回数据的 getter，但是有了 getter 就意味着您可以随时改变数据的表示或使用方式。

这在 Java 这种死板的语言中很有意义。Java 就是不太灵活，所以从一开始就添加 getters 会花费你很多时间。尤其是当大量 Java 代码在项目间重用时，拥有一个标准的命名约定(比如 getters)真的可以简化很多部分。

而且 Java 也有类型。如果你想改变某段数据的数据类型，它会破坏所有依赖于旧版本的代码。但是如果所有的东西都使用 getter，你可以保留旧的 getter，用不同的名字做一个新的 getter，让所有的东西都运行得很好。

还有一个想法是，如果你只在 Vuex 中使用 getters，你永远不会不小心设置这个值。从技术上讲，你可以在 Vuex 存储中设置状态，但这是一个非常糟糕的想法(正如我在[中解释的，为什么你只能通过突变来改变 Vuex 中的状态？](https://jerickson.net/why-should-change-state-vuex-mutations/))。只使用 getters 可以避免您意外地这样做，因为它会抛出一个错误，而不是让您这样做。

编辑: [Alexander Van Maele](https://dev.to/atlesque) 在 dev.to 的评论中指出，当试图访问状态中深度嵌套的材料时，使用 getters 也非常有用。

> 当访问超过两个级别时，我通常喜欢使用 getter。所以 state . selected order . delivery time . date 变成 getters.deliveryDate

使用 getters 的另一个很好的理由是，这可以大大提高组件的可读性。

### 是的，你应该

有些人(包括我)会说，如果这就是你所需要的，你应该访问状态。为什么要给应用程序增加不必要的复杂性呢？你的代码行越多，bug 可以隐藏的地方就越多。只有在绝对必要时才增加复杂性。在这种情况下，当数据在使用前需要过滤或格式化时。这和为什么你写代码只是为了通过最近的测试是一样的。许多面向对象的设计师也相信这种方法，包括我最喜欢的[桑迪·梅斯](https://www.sandimetz.com)。只写你需要的代码，而不是你认为你可能需要的代码，也许是某个时候，但不是现在。代码设计更加有机地发生，因为你在进行重构的同时，也在观察你在添加新代码时可以增加的效率。

(题外话:我强烈推荐 Sandi 的书[实用的面向对象设计](https://www.amazon.com/gp/product/0134456475/)给任何正在寻找如何设计他们的应用程序的开发者。它侧重于面向对象和 Ruby 语言，但是如果你想进入下一个开发阶段，其中的原则是一流的。)

有了这些原则，未来的改变就容易了。需要使用 getter 来代替直接状态吗？只需搜索并替换它。代码编辑器现在在这方面非常强大，在你的项目中的每个组件中把`$store.state.clickCount`改成`$store.getter.clickCount`可以在几秒钟内完成并测试。JavaScript(甚至是 TypeScript)不像 Java 那样严格。充分利用这种灵活性，不要拘泥于用其他语言做事情的正确方式。

Java 一直使用 getters 的另一个原因是因为 Java 也使用 setters 来设置数据。如果他们给了变量直接访问权，那么最终验证或限制对变量的写访问是不可能的。当谈到 Vuex 时，我们的 setters 是[突变，我已经谈过为什么这些对使用](https://jerickson.net/why-should-change-state-vuex-mutations/)很重要。在实际设置之前，它们也是对数据进行验证或其他检查的好地方。

## 如此...

我认为许多只通过 getters 访问数据的建议是试图将其他语言的经验应用于 JavaScript 和 Vue，我不完全确定它们是否总是适用。我的主要目标总是简单，有时直接访问状态更简单。如果不是，我可以添加一个 getter，然后在代码中运行搜索和替换。简单明了。

也就是说，我认为您将通过 getters 访问大多数数据。它们在过滤和格式化方面非常强大，大量数据将从过滤和格式化中受益。

但是许多开发者用不同的方式做这件事，很难说谁是错的，谁是 100%正确的。最终的决定取决于你。