# 用 Google Flutter 构建一个复杂的移动应用

> 原文：<https://dev.to/zoebourque/building-a-sophisticated-mobile-app-with-google-flutter-jk5>

几年前，我们在 Swift 开发了 [Quire](https://quire.io) iOS 应用程序。去年，我们选择了 [Flutter](https://flutter.io/) 来开发 [Quire Android 应用](https://play.google.com/store/apps/details?id=io.quire.app)。在这篇文章中，我想分享我用 Flutter 开发 Android 应用程序的经验——好的和坏的，优点和缺点。

## 我们是谁

我是 Quire 的前端开发人员，Quire 是一个简单、轻量级的项目管理工具，用于捕捉想法、管理任务和与团队协作。多年来，我们在我们的服务器和网络上使用 [Dart](http://simonpai.github.io/2014/09/03/quire-building-with-dart/) ,所以我们在这里，用这个使用 Dart 编程语言的新开源移动开发框架 Flutter 构建我们的 Android 应用程序。自从它在 Play Store 正式推出以来已经过去了两个月，我相信是时候让我们分享一下与 Flutter 的旅程，提供一些反馈和想法，并希望对 Flutter 社区或有兴趣加入它的人有所启发。

## 为什么会飘起？

使用 Flutter 的一个主要原因是我们希望使用单一的语言和相同的平台来简化我们的开发。Quire 是一个进化很快的应用；我们几乎每周发布一次新的更新，如果不是每天的话。随着时间的推移，维护代码的两个副本已经成为一种负担。起初，我们尝试了所谓的混合移动应用程序方法，如 Cordova 作为解决方案，但最终的用户界面和 UX 没有达到我们的目标。另一方面，Flutter 具有高性能的 UI 渲染、平滑的过渡字符和一种核心语言:Dart，其模型在所有服务器、web 和移动端共享。Flutter 满足了我们开发高质量、单代码库和快速开发周期的要求。

## 什么是颤振？

Flutter 是 Google 为 Android 和 iOS 应用开发的 UI 框架。我们可以只写一次 UI 代码，然后在两个平台上运行。它还提供了一个到 native 的桥梁，所以你可以做 Swift/Kotlin/Java 做的几乎所有事情。颤振的核心概念是拉伸和桥接，如下所述:

## 绘制画布

Flutter 直接在 iOS 的 UIViewController 和 Android 的 Activity 中的画布上绘制 UI。我们的 Dart UI 代码会被编译成机器码和图纸。这就是为什么 Flutter 有平滑的 UI 和过渡。如果我们将其与 CSS 进行比较，他们使用更简单的布局模型，这比 CSS 的复杂布局模型要好。

## 桥

如果我们需要访问每个平台的资源，我们可以使用桥将我们的 Dart 命令和数据传输到本机级别，反之亦然。因为我们是在 Flutter 环境中的画布上绘制，所以不需要使用到本机代码的桥，这降低了上下文切换的成本，比 React Native 等其他混合框架的成本低得多。

## 颤振与 iOS SDK

Flutter 是一个开源框架，这意味着您可以快速了解每个 API 调用中发生了什么。此外，我们可以追溯整个系统的架构和机制。如果你正在使用一个 iOS SDK，那么你可能需要阅读无数的书籍，从最简单到最难，反复试验这么多次，从而能够最终找到真正的，底层的逻辑规则。

## 语言水平

如果你在 Swift 有几年的经验，你可能听说过 Swift 的本地推理特征。但不代表 SDK 级别也有一样的。例如，当我们需要为基于 UIView 的组件设置委托或者为函数调用设置回调时，大多数情况下，由于委托模式的原因，相关的操作流程总是在不同的部分。回调模式也会导致回调地狱问题。

你可能会问，Swift 中最好的异步模式是什么？回调？GCD？PromiseKit？或者甚至是反应迅速？似乎没有完美的解决方法。有了 Dart，我们只需要这样做:

```
Future scrollToComment(Comment comment) async {
  await model.scrollTo(comment.position);
  await model.highlight(comment);
}
That’s the truth of local reasoning. Right? 
```

斯威夫特因为建造时间又被扣了一分。三年前，我们开始使用 Swift 进行模型移植和 iOS UI 实施。随着编译时间一天天增加，我们的代码库最终变得越来越大。没有什么比期待某件事在瞬间发生却比预期的要长更痛苦的了。

我们大概可以忍受 2 到 3 分钟的编译时间，因为这个过程是自动的，不会经常发生。但是，如果我们只是更改一行代码来进行样式更新并检查结果呢？最坏的情况，我们要等一分多钟！

你可能会看到有很多文章是关于通过改变你的语法来提高编译时间的，这实际上违背了我们使用一种新语言来获得更清晰的语法和更高的生产率的原因。Dart 不仅有超前的(AOT)编译器来优化产品发布的速度，还有一个 JIT 编译器来实现快速开发。现在更新一行代码，大多数情况下只需要 0.5 秒。我们对结果很满意。

## 框架层次

在界面构建器(IB)中使用故事板来构建 UI 就像梦想成真一样。我们只需要拖放创建部件，一切都会完成。但是在现实世界中，UI 并不是一件容易完成的任务，尤其是当你听到有人建议你将文件故事板保持得尽可能小，或者干脆不要使用它。

当达到它的限制和性能影响时，我们最终决定停止使用 IB。但是在 iOS 中以编程方式构建 UI 也是一场噩梦。例如，UI 组件、自动布局、遗留布局和过渡需要的代码比您预期的多；代码块看起来杂乱无章，你总是需要阅读大量的文档来确保你的实现符合每一条规则。

Flutter 在 Dart 2.0 中使用“代码作为 UI 模板”，就像 JSX/XML/HTML 风格一样构成 UI。这使得维护 UI 代码变得很容易。

```
Container(
  child: Center(
    child: Row(
      children: [
        Icon(‘smile’),
        Text(‘Hi’, style: TextStyle(color: Colors.red))
      ]
    )
  )
) 
```

iOS 官方解决方案中的布局对我来说一直没有意义。iOS 中的第三方解决方案永远是这场战役的赢家。对我来说，Flexbox 比类似 AutoLayout 的解决方案更好。它的 UI 编写更加简单和直观。Flutter 将 Flexbox 概念用于布局模型。此外，还有一个文档指导 web 开发人员的每一步。作为一个多年的 web 前端开发者，这显然是个好消息。

在我们的情况下，Quire 的情况下，从/到 native 的桥梁是最后一道防线。我们始终牢记，如果没有其他解决方案，我们至少可以像本地 iOS/Android 开发者那样做。这保证了即使在最坏的情况下，我们也可以交付任何功能，因为我们使用的是测试版框架(在我们开发提交给 Play Store 的第一个版本时，它实际上仍处于 Alpha 阶段)。例如，我们发现使用 Dart 压缩一张照片的时间非常长(大约 50 秒，70%的图像质量)。用 Java 代码，只需要 0.5 秒。

## 要注意的事情有扑

Flutter 仍处于测试阶段，正在快速发展。我们应该记住，事情可能会毫无保证地发生变化。下面，你会发现一些我认为缺失的特性，这些特性应该被 Flutter 在未来的版本中考虑。

## 还没有滚动到索引 API

如果您使用的是 ListView，您只能通过给定滚动偏移量来滚动该视图。固定行高的情况很容易，但是对于各种行高的情况，要做到这一点就有点复杂了。我们在 Quire 应用程序中的想法是

## 给每一行一个索引。

滚动一个恒定的距离，检查生成了这些小部件的哪个状态，以便查看当前的范围。多次搜索步骤 2，直到我们的目标行出现。
在超长列表的情况下，为了优化其平滑度，我们引入了推荐的行高变量。基于行高的滚动将确保在长列表中滚动更加准确和平滑。

## 建模流程并与 UI 绑定 InitState 和 Dispose

模型绑定的设计应该确保模型可以被多次收听并且是可计数的。根据我们的经验，您可以在 initState 中绑定它，在 dispose 中解除绑定，并在绑定存在且没有任何侦听器的情况下启动/停止模型操作。确保绑定时不发出任何事件(例如 initState 中的 Fire 事件)。为什么？由于 initState/dispose 状态正在执行，该事件将导致其他侦听器接收该事件并更新状态，而上下文范围被锁定。

## 不缓存 Widget 构建是 Flutter 的核心理念

建筑成本没有你想象的那么贵。如果你缓存它，你也必须处理你的清理。让作品飘动；它可以使用 React 概念、diff 来实现这一点，并且只更新必要的内容。在我们的例子 Quire 树视图中，我们在 ListView 中测试了 2000 多行(由于某种原因，我们没有使用 ListView 的构建器解决方案)。由于有状态小部件，它比我们预期的要快得多，当它在视口中时，它只生成行状态。对于构建缓存，Flutter 已经发表了一篇文章。

## 大多数 iOS 外观的小工具还没有准备好

Flutter 目前专注于材料设计组件。在 iOS 中使用它们没问题，因为材料设计通常是为跨平台设计的，但在某些情况下，它不如在 Android 中好。以基于轮子的日期选择器为例。总的来说，我认为仍然有必要提供与 iOS 中的原生行为相匹配的用户体验。

## 输入在颤振中

有许多与输入相关的问题。比如在 issue [#13765](https://github.com/flutter/flutter/issues/13765) 中，在你输入更多的单词之前，你应该能够看到新的一行；在问题 [#5986](https://github.com/flutter/flutter/issues/5986) 中，没有机会知道用户输入了什么键。

## 结论

Flutter 是一个用于创建 Android 和 iOS 原生应用的强大框架。我们在开发我们的[项目管理软件](https://quire.io) Android 应用程序时享受到了它，当它正式发布时，我们会更加享受它。即使是在 Alpha 和现在 Beta 的时候，Flutter 一直都很稳定。它的开发者也非常积极地回答你的任何问题。

作为一个开源框架，它可以让你轻松地跟踪正在发生的事情，以及已经修复和更新的内容。你甚至可以自己解决问题，为社区做贡献！flutter——一个带有本机行为的高性能跨平台框架——绝对是您的最佳解决方案。我们目前正计划在未来几个月用 Flutter 替换我们基于 Swift 的 iOS 应用程序，届时我将再次分享我们的经验。坚持下去，扑扑，你绝对牛逼。