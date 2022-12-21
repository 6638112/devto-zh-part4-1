# 更好的前端评论

> 原文：<https://dev.to/rfornal/better-front-end-comments-365e>

注释包括人类可读的描述，提供关于代码应该做什么的细节。正确使用注释可以使代码维护变得非常容易，并且可以更快地找到错误。此外，在编写将由其他开发人员处理的代码时，注释也很重要。

你有没有写过代码，但是六个月后看着它却不知道它是如何工作的？

当编写代码时，复杂的逻辑经常会出现；这是一个在代码中包含注释来解释逻辑的机会。无论开发人员如何开发代码，都会有注释来帮助理解逻辑。

在大型项目上花费过时间的开发人员理解注释的重要性。当你自己开发或者在团队项目中开发时，通过注释来记录代码是必要的，这并不奇怪。最终，开发人员应该致力于清晰、易读的注释，以进一步解释代码库的混乱区域。

## 注释代码的方式

### 屏蔽注释

块注释应该放在函数的顶部，描述代码的用途。

当需要大量的解释时，通常块注释会起作用。描述块在函数和库文件中最明显。

### 行内注释

应该谨慎使用行内注释，只有在代码不是“自文档化”的情况下。将它们放在任何不能自我解释的代码之前(或旁边)。该注释应该详细说明代码背后的“想法”以及要完成的任务。如果“算法”是复杂的，它也可以说这是如何完成的。

开发人员应该避免过分使用内联注释，因为我们通常不需要在整个代码中看到注释

## 应该注释什么

开发人员通常了解的关于基本 HTML 或 CSS 的事情之一是如何在代码中编写注释。然而，许多开发者仍然没有有效地使用注释。HTML 和 CSS 中可能会有注释...但是如果写得恰当，并且有意图，这些评论确实可以改善工作流程。

一个新的开发人员可能会发现阅读手册或许多页的文档令人望而生畏。每个公司都不一样...这意味着代码库、遗留代码的数量、框架的开发和模块化代码的数量将会不同。

开发人员首先说，“好的代码不需要注释。”话虽如此，开发人员经常发现自己在原地打转，完全不知所措，并且因为缺少注释而搜索文档。

### 关于代码注释的两个事实

1.  浏览器会忽略注释。
2.  在缩小和篡改过程中，注释被删除。

基于这两个事实告诉我们，评论并不真的是为机器准备的...它们是给人类阅读的。

### HTML

HTML 注释以`<!--`开始，以`-->`结束。查看页面源代码的任何人都可以看到 HTML 注释，但是当浏览器呈现 HTML 文档时，不会呈现这些注释。

#### (HTML 的)逻辑分组

保持 HTML 组的逻辑组织，并提供注释，说明以下分组的 HTML 属于什么。

### CSS

CSS 只利用用`/*`和`*/`描述的块注释。请记住，注释将公开显示给访问者，因为 CSS 不是在服务器端解析的，但是这种方法对于在代码库中留下信息性的花絮来回顾非常有用。

然而，CSS 缺少行内注释语法。

#### 解释为什么可能需要`!important`

当`!important`包含在代码中时，开发人员通常认为他们看到的是遗留代码或肮脏的黑客行为。

#### (CSS 的)逻辑分组

将样式组织在逻辑组中，并提供注释，说明以下样式属于什么。

### JavaScript

为了在 JavaScript 中创建一行注释，在 JavaScript 解释器应该忽略的代码或文本前面加了两个斜线`//`。当使用这两个斜杠时，它们右边的所有文本都将被忽略，直到下一行。

这些类型的注释非常适合注释掉单行代码和编写小笔记。

对于大注释，JavaScript 的多行注释以`/*`开始，以`*/`结束。

### JSON

这就是道格拉斯·克洛克福特所说的从 JSON 中移除评论。

> 我从 JSON 中删除了注释，因为我看到人们用它们来保存解析指令，这种做法会破坏互操作性。我知道评论的缺失让一些人难过，但不应该。
> 
> 假设您正在使用 JSON 保存配置文件，您希望对这些文件进行注释。继续插入所有你喜欢的评论。然后通过 JSMin 将其传递给 JSON 解析器。

### 提交消息

当使用版本控制系统(比如 Git)时，开发人员应该利用他们所知道的在代码中编写有用的注释，并将其应用到提交消息中。

错误的提交消息没有给出太多的上下文。它们看起来很草率，而且通常很难理解。它们作为发行说明并没有什么帮助，而且很难找到。开发人员也很难知道提交中发生了什么变化。

## 自我记录代码

自记录代码的目标是使用精心选择的变量(和函数)名称，使代码尽可能接近人类可读。通过使用适当的变量和函数名，开发人员可以最大限度地减少所需的“外部”文档的数量。

> "好的代码是自我记录的."

这种说法有一点真实性。但是这个真理被如此频繁地滥用，以至于大多数说出这句话的人都不知道它真正的意思。

是真的吗？**是**

这是否意味着开发人员永远不应该在代码中添加注释？**否**

首先，有记录系统的代码；这可以忽略不计。然后，有一些代码阐明了不应该被排除在代码库之外。

澄清注释适用于任何可能需要维护、重构或扩展代码的人(包括未来的自己)。

通常，这些澄清注释是一种代码味道。它应该告诉开发者代码太复杂了。开发人员应该努力删除澄清注释并简化代码，因为“好的代码是自文档化的”

尽管如此，有时无论开发人员对代码本身做了什么，澄清注释仍然是必要的。

## 注释代码很重要

评论有助于保持一致性。对于正在构建的东西，一致的、写得好的评论每次都会以同样的方式加强构建。

**注释便于理解。**这在团队中非常重要，因为有时一个人无法完成所有的工作。开发人员可能会编写注释来帮助自己找出一些逻辑，即使他们的所有注释都没有保留在项目中，也可以帮助更好地理解他们是如何得出解决方案的。它有助于以后改进该解决方案。

评论还有助于热修复或快速修复。在这里，评论实际上可以在三个方面有所帮助。

1.  如果开发人员需要快速解决问题，他们可以帮助他们理解代码(尤其是前端团队以外的开发人员，他们可能会提供帮助)，
2.  它可以通过标记出哪里需要这些修复来提供帮助
3.  它可以显示哪里应用了快速修复，哪里需要在某个时候删除。

评论有助于加快开发过程。如果有相关的评论，开发人员将会对正在创建、更改或删除的内容有一个更清晰的了解。

评论有助于更有效的协作。当开发人员了解项目或代码库的来龙去脉时，他们更有可能更快地完成工作，从而改进工作流程。

评论帮助了很多人。他们不仅帮助最初的开发人员，还可以帮助团队中的其他人。

## 更好的评论风格

1.  保持一切可读:开发人员有时会忘记他们正在写评论给人们阅读。
2.  分配空间:空白非常重要。对于在拥有数百个文件的大型网站上工作的开发人员来说，更是如此。他们整天盯着这个代码。
3.  **边编码边评论**:加上适当的间距，这可能是最好的习惯之一。没有人想在他们的程序运行后回顾它并记录细节。
4.  **处理 bug 和错误**:开发人员有时会留下一些仍然有缺陷的代码库，计划重新开发代码。在这种情况下，他们留下关于东西放在哪里的详细评论是至关重要的。

## 结论

关于如何在前端代码中格式化注释，没有硬性的规则。要包含的信息由开发人员决定，或者可以由开发人员和他们的同行决定。只要他们保持格式一致，就能保持整洁，并鼓励从事代码工作的其他人也这样做。

将注释作为开发过程的一部分有很多好处。养成适当地包含它们的习惯是很好的，尤其是当很多人在同一个代码库中工作的时候。

注释是开发人员交流代码意图的重要部分。严格的规则(每个服务和功能的代码)会像完全依赖自文档代码一样容易破坏这种交流。对于开发过程来说，好的注释与好的代码一样重要。