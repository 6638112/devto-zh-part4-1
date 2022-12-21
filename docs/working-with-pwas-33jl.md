# 使用 pwa

> 原文：<https://dev.to/flippedcoding/working-with-pwas-33jl>

很有可能你正在你的手机或其他移动设备上阅读这篇文章。每天都有越来越多的人通过手机上网。很方便，也不会变。移动不再是未来，它就在眼前，我们必须不断学习新技术，使我们的网络应用程序更加灵敏。这是渐进式网络应用(PWAs)越来越受欢迎的原因之一。

最棒的是，它们创建起来并不困难，而且你不必对你的代码做很大的改动。最重要的是，有很多工具可以用来衡量你的 web 应用程序到底有多先进。当你把你的网络应用做成 PWAs 时，你会得到一些非常酷的功能。这是关于 pwa 是什么，为什么我们要制作它们，以及如何实际制作一个有角度的 pwa 的快速演示。

## 什么是 PWA

渐进式网络应用比听起来要简单得多。下面是一个让网络应用进步的列表:

*   你的网站遵循 HTTPS 协议
*   这些页面可以在包括平板电脑在内的各种移动设备上响应
*   你的网站可以跨浏览器运行
*   过渡不应该感觉缓慢
*   当应用程序离线时，所有的网址都会加载
*   有添加到主屏幕的元数据
*   第一批货真的很快
*   每个页面都有一个 URL

这个列表是你做一个简单的 PWA 所需要的一切。这些步骤看起来都不难，对吗？这是因为这些事情的前一半是你应该在任何 web 应用程序中遵循的最佳实践。如果你想知道，让过渡感觉更快意味着你给了用户某种反馈，就像一个加载轮，当他们等待页面加载时。

清单上的另外四件事才是真正让人们认识到 pwa 的好处的。你需要元数据，这样用户就可以把你的网站保存到他们的主屏幕上，就像一个应用程序出现一样。我们将使用 manifest.json 文件来完成这项工作。你可以让应用程序离线加载，并与服务人员进行一些很酷的缓存。让你的应用程序第一次加载真正快速只是测试和优化代码。最后，如果你正在开发一个单页面应用程序(SPA ),给每个页面一个自己的 URL 可能会很棘手，但是应该不会非常困难。

现在你知道 PWA 是由什么组成的了。这是一个遵循最佳实践的 web 应用程序，可以离线加载，运行速度很快。进步的部分来自于这样一个事实，你可以慢慢地升级你现有的应用程序，使它们成为 PWAs。很可能你已经完成了前四件事，这意味着你已经完成了一半。

## 何苦做一个

渐进式网络应用已经成为一个如此热门的术语，以至于很难记得我们最初为什么会关注它们。它们使所有设备上的移动浏览更像本机，而不需要额外的代码库。根据您的应用程序，您可能只需要一个 PWA，而不是构建移动应用程序。一些应用程序不需要超级性能或权限就可以在设备上进行更改，因此 PWA 将是一个很好的选择。

当你构建你的应用时，你可以从 PWA 开始，这样就有可能避免制作原生移动应用的需要。这是你会费心制作 PWA 的主要原因。一旦你让它变得有响应性，你就不需要采取更多的步骤，这些好处值得你付出额外的努力。

## 如何制作 PWA

现在它是你一直在等待的。我们将使用 Angular 7 制作一个非常简单的 PWA。如果您没有安装 Angular CLI，并且想要继续操作，请确保在您想要创建的项目的目录中运行该命令。

```
npm install -g @angular/cli 
```

Enter fullscreen mode Exit fullscreen mode

然后，您可以通过运行此命令快速创建 Angular 7 应用程序。

```
ng new client 
```

Enter fullscreen mode Exit fullscreen mode

我通常把我的前端东西叫做“客户端”，但是你可以把你的新应用命名为任何你想命名的东西。Angular 使得制作 pwa 变得非常容易，就像大多数流行的框架一样。您可以运行此命令使您的新 Angular 应用程序或现有应用程序渐进。在运行之前，请确保您位于根目录中。

```
ng add @angular/pwa 
```

Enter fullscreen mode Exit fullscreen mode

这为你增加了一些东西。您将获得一个可以编辑的预生成清单文件，一个为服务人员设置配置的 ngsw-config.json 文件，ServiceWorkerModule 将导入到应用程序中，但仅在您进行生产构建时使用。这给了你 PWA 清单上接下来的两件事！

最后两项取决于您希望如何运行您的项目。有很多方法可以加速你的应用程序，比如缩小文件或者延迟加载，处理 URL 超级依赖于你如何处理路由。这可能会生成应用程序的大部分 URL。

如果你注意到了，我们不需要编写任何额外的代码来将这个新的 Angular 应用程序变成 PWA。你所要做的就是运行一个 ng 命令，然后嘣。你有一个正常工作的 PWA。现在，您可以构建您的应用程序，并在生产模式下运行它，以查看它的运行情况。查看 PWA 是否工作的一个快速方法是检查服务人员是否有空。

您可以在 Chrome Dev 工具中通过进入应用程序选项卡，然后检查服务人员面板来完成此操作。如果你看到有服务人员，你的 PWA 正在工作！现在你所要做的就是像平常一样构建你的应用程序，记住响应设计，并让你的其他角组件流动起来。

当你从一个全新的应用程序开始时，很容易说制作 PWA 是多么简单。复杂的地方在于，当你试图升级一个现有的应用程序时，它可能会响应，也可能不会响应，它可能不是跨浏览器的，或者它可能会出现快速加载的问题。这时你必须重构代码和更新包，这会变得很混乱。

更别提服务人员有多奇怪了。你是否需要升级一个应用程序，Angular 或其他什么，以成为一个进步的 web 应用程序？对于正在经历这一疯狂过程的人，你有什么有趣的故事或建议吗？我会说，你应该首先确保应用程序是有响应的。这可能会花费最多的时间，并且会对用户体验产生巨大的影响。

* * *

嘿！你应该在推特上关注我，因为原因:[https://twitter.com/FlippedCoding](https://twitter.com/FlippedCoding)