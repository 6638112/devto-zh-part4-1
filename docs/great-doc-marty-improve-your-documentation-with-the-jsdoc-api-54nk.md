# 伟大的医生马蒂！使用 JSDoc api 改进您的文档

> 原文：<https://dev.to/keevcodes/great-doc-marty-improve-your-documentation-with-the-jsdoc-api-54nk>

# 哇哇 Doc，好重。

文档是我们代码中最重要的部分之一。我们的社区反复提到写好的文档如何帮助我们所有人，以及坏的文档对使用我们项目的其他人有多么有害。然而，编写好的文档并不容易，需要一些时间来做好。在我今年早些时候的最后一次性能回顾中，来自我的团队领导的一个建设性的反馈意见是改进我记录代码的方式。

在这一年中，我一直在思考如何在这一点上有所改进。我开始把更多的精力放在如何命名函数和变量上。我还开始在编写特定代码时注释掉我的思维过程，然后在创建 PRs 之前清理这些注释。这两个实践都很有帮助，但是后来我在和我团队的几个成员开始一个新项目时遇到了一个非常有用的工具。

您是否曾经阅读过一些代码，并遇到过这样的代码片段？

```
 /**
    * Transform
    * @param {String} ID - page identification
    * @returns {object}
    */

    function transform(ID) => { 
       return { pageName: ID, title: 'Hello World'}
     } 
```

Enter fullscreen mode Exit fullscreen mode

起初，我很困惑，不知道这一切都是为了什么？见鬼，说实话，用这种方式写评论看起来很奇怪。经过一番挖掘，我发现这些东西是从哪里来的；一个叫做 JSDoc 的 API，是 phpDocumentor 和 Javadoc 的子集。

JSDocs 列出了一些在记录我们的代码时要遵循的指导方针，一旦我们理解了它是如何工作的，我们就可以用它来帮助生成我们代码中最重要的部分之一，文档。

# 我们要去的地方，确实需要道路

让我们从 JSDocs 的一些基础知识开始。看看上面的例子，我们注释的整个结构(`/** **/`位)被称为文档块，那些`@param`行被称为块标签。文档块通常出现在我们的代码之前，我们使用块标签来提供关于我们的代码正在做什么的细节。DocBlock 也可以放在任何文件的顶部来记录主要代码，只是要注意这个块应该在任何其他块之前，它之后的任何块应该是独立的。

然而，我们并不仅限于在块标签中标注函数参数。JSDocs API 为`@functions`、`@contractors`提供了标签，以标识我们代码的`@liscense`和`@ignore`来从我们的文档中排除一些代码。访问 [JSDoc 文档](https://devdocs.io/jsdoc/index#block-tags)查看 JSDocs 提供的所有不同标签。

# 回特征

许多现代的 ide，如 VSCode，将支持 JSDocs 文档化代码的自动完成，提供对代码的使用洞察，同时节省我们的时间！

另一个很棒的特性是，当我们完成我们的应用程序/库时，JSDocs 提供了一个默认的 HTML 文件`layout.tmpl`，其中包含了我们的 DocBlocks 中提供的所有信息！这个文件也是完全可配置的，允许定制样式。

说到配置 JSDocs，在我们的文档块中对 markdown 格式代码的支持也可以通过我们的配置文件中的`"plugins": [plugins/markdown]`获得。

# 结论

好的文档对于你正在进行的任何项目都是必不可少的，尤其是如果你打算与他人分享的话。虽然写作永远是一个不断发展的过程，但有一些工具可以帮助你朝着正确的方向前进。我希望您考虑将 JSDoc 或另一个文档 API 添加到您的工具箱中。感谢你的阅读，如果你喜欢这篇文章，请给它一个赞或发微博。