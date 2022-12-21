# 给那头牦牛剃毛！

> 原文：<https://dev.to/joshuagilless/shave-that-yak-484>

我一直最喜欢的表达之一是“牦牛剃毛”。它让我发笑。想象自己拿着和我刮胡子用的一样的电推子，试着把这头大牛的毛剪掉，这是一种超视觉的感觉。说实话，我甚至不确定我在纪录片之外见过牦牛，所以我只是想象一只拥有美丽飘逸长发的大牛(母牛长发公主？).

这个短语的起源是一个叫卡林·维耶里的人，他当时在麻省理工学院。杰里米·h·布朗的一封电子邮件解释道:

> 你看，剃牦牛毛是你在做一些愚蠢的、繁琐的小任务，这些任务与你应该做的事情没有明显的关系，但十二个因果关系链将你正在做的事情与最初的元任务联系起来。

一些人，比如 Seth Godin，在他的博客文章[“不要给那头牦牛剃毛”](https://seths.blog/2005/03/dont_shave_that/)中反对这种做法。其他人，像 Florian Gilcher，指出[好东西来自给牦牛剃毛](https://yakshav.es/the-patron-saint-of-yakshaves/)。

我的博客本身就是一头牦牛。我决定要写一篇博文。然后我决定我不想使用 Wordpress 或 Drupal，从那以后一切都走下坡路了。我决定它必须是我自己设计的应用程序。很久以前，在我看了 [DHH 的](https://twitter.com/dhh)名人在 15 分钟内建一个博客的演示后，我用 Ruby 写了一些博客软件。但是我不想用 Ruby 写博客，因为我以前已经这样做过了。在工作中，我们使用一种叫做 Go 的很酷的语言。

我真的很喜欢围棋。我一直在做一些小的玩具应用程序，这些程序可以连接到数据库，或者验证 jwt，或者处理一般的互联网事务。我建立了一个小的网络爬虫来做 SEO 审计，我建立了一个小东西来处理 OAuth 到 Google，然后用客户端 JWT 的持久化它。不过，这些都没有真正整合到博客软件中。

每次我试图开始写博客软件时，我都会四处寻找 Go 中路由的学习资源。我经常看到有人说“你只需要标准库”之类的话。所以我试了几次，用标准库开发了几个小型路由器，它们最多也就可以了。我不喜欢我最终使用它们的方式，所以我一直使用 Gorilla 或 Echo。

反正我决定从底层开始写软件。因为我已经在用围棋了，所以我看了看[app engine](https://cloud.google.com/appengine/)——两者都是谷歌做的，所以他们*有*可以一起下围棋。我知道我想要一种写文章的方式，这意味着我需要一种持久化数据的方式，一个数据库。我以前没有用过 NoSQL DB，所以我想试试 NoSQL。谷歌云有一个名为 Datastore 的 NoSQL 数据库，但当我开始这个项目时，它被一个名为 [Firestore](https://cloud.google.com/firestore/) 的数据库所取代，所以我想，我们就用 Firestore 吧。

我阅读了文档，很快就开始运行了，但是我知道我需要一种向 Firestore 发布数据的方式。所以我开始写一个小的 CMS 来登录和发布东西。Firestore 把我带到了 Firebase，我最终不知从哪里冒出来了 Firebase Auth，因为我决定使用 Firestore。效果很好！我甚至想过把整个应用程序做成 SPA，并通过同一个程序显示帖子。

回去吧。我编写了一个与 Firestore 接口的服务器端应用程序。它使用基本的 IAM 管理来保护它。它不包括 Firebase 的 JS，因为这个包很大，我不想这么做。我还用标准库在 Go 中写了一个路由器。它不是很好，我不会推荐其他人使用它。另一方面，我真的很高兴我一头扎进去，编写了足够的服务器代码来让某些东西工作。

用一种你并不真正了解的语言写一个你自己的路由器和写一篇博客文章是非常不同的。在这些看似不相关的任务中，我学到了很多很酷的东西，因为我愿意跟随牦牛直到我得到我想要的。我写了一个 CMS，我写了一个路由器，我写了一堆模板，所有这些都是为了让我可以对着以太大喊大叫。

牦牛毛也发生在现实生活中，而不仅仅是在编程世界中。有时候，你最终会跟随一连串看起来与你应该做的事情毫不相关的任务。但是如果你从这些任务中学到了东西，并且能够恢复到你应该做的事情，那么这些任务就值得去做。

而不是只说“别给那头牦牛剃毛！”，弄清楚是否有值得学习的东西，沿着链条走，直到你不得不剃牦牛毛。因为有时候给牦牛剃毛是正确的。